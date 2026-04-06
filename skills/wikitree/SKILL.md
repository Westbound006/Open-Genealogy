---
name: wikitree
description: >-
  Query WikiTree profiles, explore ancestors and descendants, find research
  gaps in your family tree, and search for people. Use when the user wants
  to look up, browse, or analyse WikiTree data.
license: MIT
compatibility: Claude Code
metadata:
  version: "1.1.0"
  api: WikiTree API (read-only, public profiles)
  api_endpoint: https://api.wikitree.com/api.php
---

# WikiTree Skill

Read-only access to WikiTree profile data. Looks up profiles, explores
ancestor and descendant trees, finds research gaps, and searches by name.

**This skill only reports what WikiTree returns. It never invents people,
dates, places, or relationships.**

## User Defaults

| Setting | Value |
| ------- | ----- |
| Default WikiTree ID | `Philpott-1879` |
| API endpoint | `https://api.wikitree.com/api.php` |

When the user says "my profile", "my tree", or "my ancestors" without
specifying an ID, use `Philpott-1879`.

## When to Auto-Invoke

Auto-invoke when the user wants to work with WikiTree data. Trigger phrases:

- "look up [WikiTree ID]"
- "show my profile on WikiTree"
- "who are my ancestors on WikiTree"
- "explore my tree"
- "find gaps in my WikiTree tree"
- "search WikiTree for [name]"
- "who is [name] on WikiTree"
- "show descendants of [ID]"
- "find [name] in the big tree"
- "check if WikiTree has [person]"

Do NOT auto-invoke for GEDCOM creation (use gedcom-creator), GPS evidence
analysis (use gra), or questions about genealogy methodology in general.

## Core Operations

All calls use `curl` via the Bash tool. The API is public and requires no
authentication for public profiles.

---

### 1. Look Up a Profile

Fetch full details for a known WikiTree ID.

```bash
curl -s "https://api.wikitree.com/api.php?action=getProfile&key=WIKITREE_ID&fields=Id,Name,FirstName,MiddleName,LastNameAtBirth,LastNameCurrent,Gender,BirthDate,BirthDateDecade,BirthLocation,DeathDate,DeathDateDecade,DeathLocation,Father,Mother,HasChildren,IsLiving,Privacy,Manager,EditCount&resolveRedirect=1&format=json"
```

**Display format:**

```
=== WikiTree Profile: [Name] ===
WikiTree ID: [Id]
Born:  [BirthDate] — [BirthLocation]
Died:  [DeathDate] — [DeathLocation]
Father: [Father.Name] ([Father.Id]) — or "not recorded"
Mother: [Mother.Name] ([Mother.Id]) — or "not recorded"
Has children: Yes / No / Unknown
Profile managed by: [Manager.Name]
Last edit count: [EditCount]
Profile URL: https://www.wikitree.com/wiki/[Id]
```

If `IsLiving` is true: display name only and note the profile is private
(living person). Do not display any other fields.

If Privacy indicates a private profile: note that full data requires
authentication and display only what the API returned.

---

### 2. Explore Ancestors

Fetch the ancestor tree from a starting profile.

```bash
curl -s "https://api.wikitree.com/api.php?action=getPeople&keys=WIKITREE_ID&ancestors=DEPTH&fields=Id,Name,FirstName,LastNameAtBirth,Gender,BirthDate,BirthDateDecade,BirthLocation,DeathDate,DeathDateDecade,DeathLocation,Father,Mother&resolveRedirect=1&format=json"
```

**Depth guide** (suggest these to the user):

| Depth | Covers | Approx. profiles |
| ----- | ------- | ---------------- |
| 1 | Parents | 2 |
| 2 | Grandparents | up to 6 |
| 3 | Great-grandparents | up to 14 |
| 4 | 2× great-grandparents | up to 30 |
| 5 | 3× great-grandparents | up to 62 |

Default to depth=3 unless the user specifies otherwise. Warn before
requesting depth 6+ as response times increase significantly.

**Display format** — present as a generation-by-generation list:

```
=== Ancestors of [Name] (to [N] generations) ===

Generation 1 — Parents
  Father: [Name] (b. [year], [place]) → [WikiTree ID]
  Mother: [Name] (b. [year], [place]) → [WikiTree ID]

Generation 2 — Grandparents
  ...

[Continue for each generation]

Total profiles returned: [count]
```

If a parent slot is empty (Father or Mother is null/0), note:
"[paternal/maternal grandfather] — not recorded in WikiTree"

---

### 3. Find Research Gaps

Fetch ancestors and flag profiles with missing or thin data that the user
could improve or look for elsewhere.

Use the same `getPeople&ancestors=` call as above with depth=4 (or user's
choice), then analyse the returned data.

**Gap criteria — flag a profile when:**

| Gap type | Condition |
| -------- | --------- |
| Missing birth | `BirthDate` is blank or decade-only (`BirthDateDecade` only) |
| Missing birth place | `BirthLocation` is blank |
| Missing death | `DeathDate` is blank and `IsLiving` is false |
| Missing death place | `DeathLocation` is blank |
| Missing father | `Father` is null or 0 |
| Missing mother | `Mother` is null or 0 |
| Low edit count | `EditCount` is 1 (only the creator has touched it) |

**Display format:**

```
=== Research Gaps in [Name]'s Ancestor Tree ===

[Count] profiles flagged across [N] generations.

--- Generation 2 ---
[Name] ([Id]) — missing: birth date, birth place
  → https://www.wikitree.com/wiki/[Id]

[Name] ([Id]) — missing: father, death date
  → https://www.wikitree.com/wiki/[Id]

--- Generation 3 ---
...

Profiles with no gaps: [count]
```

Include the WikiTree URL for each flagged profile so the user can click
straight through.

---

### 4. Search for a Person

Search WikiTree by name, with optional birth year filter.

```bash
curl -s "https://api.wikitree.com/api.php?action=searchPerson&FirstName=FIRSTNAME&LastName=LASTNAME&fields=Id,Name,FirstName,LastNameAtBirth,BirthDate,BirthLocation,DeathDate,DeathLocation&limit=10&format=json"
```

To narrow by approximate birth year, add `&BirthDate=YEAR`.

**Display format:**

```
=== WikiTree Search: "[FirstName] [LastName]" ===
[Total] total matches. Showing first [N]:

1. [Name] ([Id]) — b. [BirthDate], [BirthLocation] | d. [DeathDate]
   → https://www.wikitree.com/wiki/[Id]

2. ...

[If total > 10]: "[Total] matches found. Ask me to narrow by birth year,
location, or show more results."
```

If 0 results: suggest alternative spellings or broader search terms.
Never invent results.

---

### 5. Explore Descendants

Fetch descendants from a starting profile.

```bash
curl -s "https://api.wikitree.com/api.php?action=getPeople&keys=WIKITREE_ID&descendants=DEPTH&fields=Id,Name,FirstName,LastNameAtBirth,Gender,BirthDate,BirthDateDecade,BirthLocation,DeathDate,DeathDateDecade,DeathLocation,Father,Mother&resolveRedirect=1&format=json"
```

Default to depth=2 (children and grandchildren). Warn before depth 4+.

**Display format** — present as a generation list (same style as ancestors
but labelled "Children", "Grandchildren", etc.)

---

## Parsing API Responses

The API returns JSON. Key things to handle:

- **Status 0** = success. Data is in `profile` (getProfile/getPerson),
  `people` (getPeople with ancestors/descendants),
  or `matches` (searchPerson).
- **Status non-0** = error. Report the error message to the user plainly.
- **Redirected profiles**: if `resolveRedirect=1` and the profile was
  merged, the returned ID will differ from the requested ID. Note this:
  "[ID] redirects to [new ID]."
- **Null parent fields**: Father=0 or Mother=0 means not recorded, not
  that the person had no parents. Say "not recorded" not "unknown parents."
- **Decade-only dates**: `BirthDateDecade` like "1850s" means no precise
  date is recorded. Show the decade and flag as a gap.
- **IsLiving=1**: Do not display any personal data beyond the name.

## Error Messages

| API response | User-facing message |
| ------------ | ------------------- |
| Status != 0, "not found" | "No WikiTree profile found for [ID]. Check the ID spelling — WikiTree IDs are case-sensitive (e.g. Philpott-1879)." |
| Empty people array | "No ancestors recorded in WikiTree for [ID] at this depth." |
| curl fails / no response | "Could not reach the WikiTree API. Check your internet connection." |
| Private profile | "This profile is private. Only the profile manager or trusted list members can view full details." |

## Anti-Fabrication Rules

- **NEVER** add people, dates, places, or relationships not returned by
  the API
- **NEVER** infer a missing parent from a surname pattern
- **NEVER** merge two profiles unless WikiTree explicitly redirects one
  to the other
- **NEVER** present API data as verified — WikiTree is a collaborative
  tree and may contain errors. When presenting facts, note they come
  from WikiTree and may need independent verification.
- When data is missing, say it is missing. Do not fill gaps.
