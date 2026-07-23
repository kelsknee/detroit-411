# Neighborhood label audit

Verified the `scope` (neighborhood) labels by locating each resource's corrected
coordinate inside Detroit's **official neighborhood boundaries**
([Current City of Detroit Neighborhoods](https://data.detroitmi.gov/datasets/7050ce421a4a46829e5e52219e174dc6),
205 neighborhoods, point-in-polygon).

Most resources (454 of 468) use broad scopes — **Citywide (370), Statewide (46),
Regional (38)** — which have no single neighborhood to check. Only **14** claimed
a specific neighborhood; 12 have coordinates. All location-based mismatches have
now been corrected to the official neighborhood.

## Corrected

| Resource | Was | Now | Basis |
|---|---|---|---|
| Life Remodeled Durfee | "Durfee / Outer Drive-Hayes" | **Dexter-Linwood** | 2470 Collingwood St → Dexter-Linwood (D5) |
| Life Remodeled Durfee (`neighborhoods` array) | group "Conant Gardens / Pershing" + stale coord | group **Dexter-Linwood** + corrected coord | same |
| Life Remodeled Anchor Detroit | "Denby" | **Denby / Outer Drive-Hayes** | Serves both communities; office at 9740 McKinney is officially in Outer Drive-Hayes (D4), and Life Remodeled anchors the Denby community. |

**`scope` = service area, not office location.** Because of this:
- The three **Southwest Solutions** entries and **Detroit Hispanic Development
  Corporation** stay **"Southwest Detroit"** — their offices sit in Corktown (D6)
  by the strict boundary, but all four serve the Southwest Detroit community.
- **Rebuilding Together SE Michigan** stays **"Jefferson-Chalmers / Council
  District 4"** — that's its Detroit service area, even though its office is in
  Farmington Hills.

Tip: a `scope` can name more than one neighborhood with the "A / B" format
(e.g. "Denby / Outer Drive-Hayes"), as several entries already do.

## Verified correct (unchanged)

| Resource | Scope | Official |
|---|---|---|
| Bailey Park NDC – McDougall-Hunt | McDougall-Hunt / Poletown East | McDougall-Hunt (D5) ✅ |
| Cass Community – Tiny Homes | Dexter-Linwood / Nardin Park | Dexter-Linwood (D5) ✅ |
| Cass Community – Housing | Dexter-Linwood / Nardin Park | Dexter-Linwood (D5) ✅ |
| Joy Southfield CDC | West Side Detroit / District 7 | Warrendale (D7) ✅ |
| LA SED Senior & Youth Center | Southwest Detroit | Springwells (D6) ✅ — Springwells is within Southwest Detroit |

## Could not verify (no coordinate)

- **Rippling Hope** — scope "Northwest Detroit"; address is a P.O. Box (48227, a NW ZIP — plausible).
- **Accessibili-D** — scope "Southeast Detroit (pilot zone)"; roving service, no fixed address.

## `neighborhoods` array (the "browse by neighborhood" section)

7 curated groups. Only the Life Remodeled / "Conant Gardens / Pershing" entry was
wrong (fixed above). The other 6 groups are internally consistent with their
member orgs (Brightmoor Alliance → West Side/Brightmoor, Grandmont Rosedale Dev
Corp → NW/Grandmont Rosedale, Detroit Friendship House → Hamtramck, etc.).

Note: the lat/lng values inside this array are **unused** — the browse section
renders only name/description/phone/website, never a map pin — so they don't
affect the map. Left them corrected anyway for consistency.
