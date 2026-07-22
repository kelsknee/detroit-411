# Neighborhood label audit

Verified the `scope` (neighborhood) labels by locating each resource's corrected
coordinate inside Detroit's **official neighborhood boundaries**
([Current City of Detroit Neighborhoods](https://data.detroitmi.gov/datasets/7050ce421a4a46829e5e52219e174dc6),
205 neighborhoods, point-in-polygon).

Most resources (454 of 468) use broad scopes — **Citywide (370), Statewide (46),
Regional (38)** — which have no single neighborhood to check. Only **14** claim a
specific neighborhood; 12 of those have coordinates. Results below.

## Fixed (committed)

| Resource | Was | Now | Why |
|---|---|---|---|
| Life Remodeled Durfee (main list `scope`) | "Durfee / Outer Drive-Hayes" | **Dexter-Linwood** | 2470 Collingwood St (48206) is officially in Dexter-Linwood, D5. "Outer Drive-Hayes" is the east side. |
| Life Remodeled Durfee (`neighborhoods` array) | grouped under "Conant Gardens / Pershing", stale coord 42.4138,-83.0889 | group renamed **Dexter-Linwood**, coord → 42.381670,-83.110116 | Same location error; this array was never part of the coordinate fix. |

## Needs your decision (not auto-changed)

| Resource | Stored scope | Official (by coordinate) | Question |
|---|---|---|---|
| Life Remodeled Anchor Detroit | Denby | **Outer Drive-Hayes** (D4) | "Denby" is colloquial and the org self-identifies with the Denby community. Keep "Denby" or switch to the official "Outer Drive-Hayes"? |
| Rebuilding Together SE Michigan | Jefferson-Chalmers / Council District 4 | **Farmington Hills** (outside Detroit) | The pin is the org's *office* in Farmington Hills; the scope names its *service area*. Show the suburban pin, relabel, or hide from map? |
| Southwest Solutions – Housing Counseling | Southwest Detroit | **Corktown** (D6) | 1600 Porter St is officially Corktown / North Corktown. Keep the broad "Southwest Detroit", or use Corktown? |
| Southwest Solutions – Renter Support | Southwest Detroit | **Corktown** (D6) | same as above (same address) |
| Southwest Solutions – Earn + Learn | Southwest Detroit | **Corktown** (D6) | same as above (same address) |
| Detroit Hispanic Development Corporation | Southwest Detroit | **Corktown** (D6) | 1211 Trumbull St is officially Corktown; SW Detroit is the broader colloquial region. |

## Verified correct (no change)

| Resource | Scope | Official | 
|---|---|---|
| Bailey Park NDC – McDougall-Hunt | McDougall-Hunt / Poletown East | McDougall-Hunt (D5) ✅ |
| Cass Community – Tiny Homes | Dexter-Linwood / Nardin Park | Dexter-Linwood (D5) ✅ |
| Cass Community – Housing | Dexter-Linwood / Nardin Park | Dexter-Linwood (D5) ✅ |
| Joy Southfield CDC | West Side Detroit / District 7 | Warrendale (D7) ✅ |
| LA SED Senior & Youth Center | Southwest Detroit | Springwells (D6) ✅ |

## Could not verify (no coordinate)

- **Rippling Hope** — scope "Northwest Detroit"; address is a P.O. Box (48227, a NW ZIP — plausible).
- **Accessibili-D** — scope "Southeast Detroit (pilot zone)"; it's a roving service with no fixed address.

## `neighborhoods` array (the "browse by neighborhood" section)

7 curated groups. Only the Life Remodeled / "Conant Gardens / Pershing" entry was
wrong (fixed above). The other 6 groups are internally consistent with their
member orgs (Brightmoor Alliance → West Side/Brightmoor, Grandmont Rosedale Dev
Corp → NW/Grandmont Rosedale, Detroit Friendship House → Hamtramck, etc.).

Note: the lat/lng values inside this array are **unused** — the browse section
renders only name/description/phone/website, never a map pin — so they don't
affect the map. Left them corrected anyway for consistency.
