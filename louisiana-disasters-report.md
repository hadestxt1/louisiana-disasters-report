# Louisiana federal disaster declarations since fiscal year 2000, by parish

Source: OpenFEMA, DisasterDeclarationsSummaries, $filter state eq 'LA' and fyDeclared ge 2000. Final report: all three timed pulls (PULL 1, PULL 2, PULL 3) are complete. All three pull CSVs are byte-identical, so the tallies below are from the last good pull, PULL 3, and are the same as they would be from PULL 1 or PULL 2.

## Summary (PULL 3, last good pull)

- Rows: 2,174. Distinct disasterNumbers: 67. Parish rows: 2,158 across 64 parishes. Non-parish rows: 16, counted apart below.
- PULL 3 CSV: la-disasters-pull3.csv, 2,174 rows, SHA-256 6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599.
- PULL 1 and PULL 2 CSVs are byte-identical to PULL 3 (same SHA-256); no new declarations appeared in any later pull.
- Top-ranked parish by major disaster (DR) declarations: Lafourche, 24 DR declarations.
- Declaration dates in PULL 3 run 2000-02-15 to 2026-06-30.

## Parish table (PULL 3)

One row per parish. Columns: total declarations, DR count, latest declarationDate, then declarations by incident type.

| Parish | Total | DR | Latest | Biological | Coastal Storm | Fire | Flood | Hurricane | Other | Severe Ice Storm | Severe Storm | Snowstorm | Tornado | Tropical Storm | Winter Storm |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Acadia | 35 | 17 | 2026-01-24 | 2 | 3 | 0 | 1 | 22 | 1 | 2 | 3 | 0 | 0 | 0 | 1 |
| Allen | 35 | 16 | 2026-01-24 | 2 | 3 | 1 | 1 | 23 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Ascension | 37 | 19 | 2026-01-24 | 2 | 4 | 0 | 5 | 22 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| Assumption | 40 | 21 | 2026-01-24 | 2 | 4 | 0 | 6 | 25 | 0 | 2 | 0 | 0 | 0 | 0 | 1 |
| Avoyelles | 33 | 15 | 2026-06-30 | 2 | 3 | 0 | 4 | 19 | 1 | 2 | 0 | 0 | 0 | 1 | 1 |
| Beauregard | 37 | 18 | 2026-01-24 | 2 | 4 | 2 | 1 | 22 | 1 | 2 | 2 | 0 | 0 | 0 | 1 |
| Bienville | 27 | 13 | 2026-02-18 | 2 | 2 | 0 | 1 | 16 | 0 | 3 | 0 | 1 | 0 | 0 | 2 |
| Bossier | 29 | 14 | 2026-01-24 | 2 | 2 | 0 | 2 | 17 | 1 | 3 | 1 | 0 | 0 | 0 | 1 |
| Caddo | 28 | 13 | 2026-01-24 | 2 | 2 | 0 | 2 | 17 | 1 | 3 | 0 | 0 | 0 | 0 | 1 |
| Calcasieu | 34 | 15 | 2026-01-24 | 2 | 3 | 1 | 2 | 21 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Caldwell | 29 | 15 | 2026-02-18 | 2 | 2 | 0 | 2 | 17 | 0 | 2 | 2 | 0 | 0 | 0 | 2 |
| Cameron | 33 | 15 | 2026-01-24 | 2 | 3 | 0 | 1 | 24 | 0 | 2 | 0 | 0 | 0 | 0 | 1 |
| Catahoula | 34 | 17 | 2026-02-18 | 2 | 3 | 0 | 5 | 17 | 0 | 2 | 3 | 0 | 0 | 0 | 2 |
| Claiborne | 27 | 13 | 2026-01-24 | 2 | 2 | 0 | 1 | 16 | 0 | 3 | 1 | 1 | 0 | 0 | 1 |
| Concordia | 32 | 14 | 2026-01-24 | 2 | 3 | 0 | 5 | 18 | 0 | 2 | 1 | 0 | 0 | 0 | 1 |
| De Soto | 29 | 13 | 2026-02-18 | 2 | 2 | 1 | 1 | 17 | 1 | 2 | 1 | 0 | 0 | 0 | 2 |
| East Baton Rouge | 37 | 19 | 2026-01-24 | 2 | 4 | 0 | 4 | 23 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| East Carroll | 29 | 14 | 2026-02-18 | 2 | 2 | 0 | 4 | 16 | 0 | 2 | 1 | 0 | 0 | 0 | 2 |
| East Feliciana | 36 | 18 | 2026-06-30 | 2 | 5 | 0 | 2 | 22 | 1 | 2 | 0 | 0 | 0 | 1 | 1 |
| Evangeline | 31 | 14 | 2026-01-24 | 2 | 3 | 1 | 1 | 18 | 1 | 2 | 2 | 0 | 0 | 0 | 1 |
| Franklin | 31 | 15 | 2026-02-18 | 2 | 2 | 0 | 3 | 17 | 0 | 2 | 3 | 0 | 0 | 0 | 2 |
| Grant | 28 | 13 | 2026-01-24 | 2 | 2 | 0 | 2 | 17 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Iberia | 37 | 18 | 2026-01-24 | 2 | 4 | 0 | 3 | 25 | 0 | 2 | 0 | 0 | 0 | 0 | 1 |
| Iberville | 37 | 19 | 2026-01-24 | 2 | 4 | 0 | 6 | 21 | 0 | 2 | 1 | 0 | 0 | 0 | 1 |
| Jackson | 25 | 11 | 2026-02-18 | 2 | 2 | 0 | 1 | 16 | 0 | 2 | 0 | 0 | 0 | 0 | 2 |
| Jefferson | 40 | 21 | 2026-01-24 | 2 | 5 | 0 | 0 | 25 | 2 | 2 | 3 | 0 | 0 | 0 | 1 |
| Jefferson Davis | 36 | 17 | 2026-01-24 | 2 | 3 | 1 | 1 | 23 | 0 | 2 | 3 | 0 | 0 | 0 | 1 |
| La Salle | 28 | 13 | 2026-01-24 | 2 | 2 | 0 | 3 | 17 | 0 | 2 | 1 | 0 | 0 | 0 | 1 |
| Lafayette | 33 | 18 | 2026-01-24 | 2 | 4 | 0 | 2 | 20 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Lafourche | 43 | 24 | 2026-06-30 | 2 | 5 | 0 | 4 | 26 | 1 | 2 | 1 | 0 | 0 | 1 | 1 |
| Lincoln | 29 | 14 | 2026-02-18 | 2 | 2 | 0 | 1 | 16 | 1 | 3 | 1 | 1 | 0 | 0 | 2 |
| Livingston | 40 | 22 | 2026-01-24 | 2 | 4 | 0 | 2 | 25 | 1 | 2 | 2 | 0 | 1 | 0 | 1 |
| Madison | 29 | 14 | 2026-02-18 | 2 | 2 | 0 | 3 | 16 | 0 | 2 | 2 | 0 | 0 | 0 | 2 |
| Morehouse | 29 | 13 | 2026-02-18 | 2 | 2 | 0 | 1 | 17 | 1 | 2 | 2 | 0 | 0 | 0 | 2 |
| Natchitoches | 34 | 16 | 2026-01-24 | 2 | 2 | 1 | 2 | 21 | 1 | 2 | 2 | 0 | 0 | 0 | 1 |
| Orleans | 38 | 19 | 2026-01-24 | 2 | 4 | 0 | 0 | 25 | 2 | 2 | 1 | 0 | 1 | 0 | 1 |
| Ouachita | 35 | 18 | 2026-02-18 | 2 | 3 | 0 | 2 | 19 | 1 | 3 | 2 | 1 | 0 | 0 | 2 |
| Plaquemines | 38 | 19 | 2026-01-24 | 2 | 4 | 0 | 1 | 26 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Pointe Coupee | 38 | 18 | 2026-06-30 | 2 | 4 | 0 | 6 | 20 | 1 | 2 | 1 | 0 | 0 | 1 | 1 |
| Rapides | 37 | 16 | 2026-01-24 | 2 | 3 | 2 | 4 | 21 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Red River | 28 | 13 | 2026-02-18 | 2 | 2 | 1 | 2 | 17 | 0 | 2 | 0 | 0 | 0 | 0 | 2 |
| Richland | 28 | 13 | 2026-02-18 | 2 | 2 | 0 | 2 | 16 | 0 | 2 | 1 | 1 | 0 | 0 | 2 |
| Sabine | 29 | 12 | 2026-01-24 | 2 | 2 | 1 | 1 | 18 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| St. Bernard | 38 | 19 | 2026-01-24 | 2 | 5 | 0 | 0 | 25 | 2 | 2 | 1 | 0 | 0 | 0 | 1 |
| St. Charles | 42 | 23 | 2026-06-30 | 2 | 5 | 0 | 3 | 26 | 1 | 2 | 1 | 0 | 0 | 1 | 1 |
| St. Helena | 35 | 18 | 2026-01-24 | 2 | 4 | 0 | 2 | 23 | 0 | 2 | 1 | 0 | 0 | 0 | 1 |
| St. James | 36 | 17 | 2026-01-24 | 2 | 4 | 0 | 3 | 23 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| St. John the Baptist | 37 | 18 | 2026-01-24 | 2 | 4 | 0 | 2 | 25 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| St. Landry | 37 | 18 | 2026-06-30 | 2 | 3 | 0 | 5 | 19 | 1 | 2 | 3 | 0 | 0 | 1 | 1 |
| St. Martin | 41 | 21 | 2026-01-24 | 2 | 4 | 0 | 5 | 24 | 1 | 2 | 2 | 0 | 0 | 0 | 1 |
| St. Mary | 41 | 19 | 2026-01-24 | 2 | 4 | 0 | 5 | 25 | 2 | 2 | 0 | 0 | 0 | 0 | 1 |
| St. Tammany | 37 | 19 | 2026-06-30 | 2 | 4 | 0 | 2 | 24 | 1 | 2 | 0 | 0 | 0 | 1 | 1 |
| Tangipahoa | 37 | 19 | 2026-01-24 | 2 | 4 | 0 | 2 | 25 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| Tensas | 27 | 12 | 2026-02-18 | 2 | 2 | 0 | 2 | 16 | 0 | 2 | 1 | 0 | 0 | 0 | 2 |
| Terrebonne | 42 | 21 | 2026-06-30 | 2 | 5 | 0 | 5 | 25 | 1 | 2 | 0 | 0 | 0 | 1 | 1 |
| Union | 30 | 16 | 2026-02-18 | 2 | 2 | 0 | 1 | 17 | 0 | 3 | 2 | 1 | 0 | 0 | 2 |
| Vermilion | 36 | 17 | 2026-01-24 | 2 | 4 | 0 | 1 | 24 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Vernon | 34 | 13 | 2026-01-24 | 2 | 3 | 4 | 1 | 19 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| Washington | 33 | 16 | 2026-01-24 | 2 | 4 | 0 | 2 | 22 | 0 | 2 | 0 | 0 | 0 | 0 | 1 |
| Webster | 28 | 13 | 2026-02-18 | 2 | 2 | 0 | 1 | 15 | 1 | 3 | 1 | 1 | 0 | 0 | 2 |
| West Baton Rouge | 33 | 15 | 2026-01-24 | 2 | 4 | 0 | 3 | 19 | 1 | 2 | 1 | 0 | 0 | 0 | 1 |
| West Carroll | 26 | 12 | 2026-02-18 | 2 | 2 | 0 | 1 | 16 | 0 | 2 | 0 | 1 | 0 | 0 | 2 |
| West Feliciana | 39 | 20 | 2026-01-24 | 2 | 5 | 0 | 7 | 21 | 1 | 2 | 0 | 0 | 0 | 0 | 1 |
| Winn | 27 | 12 | 2026-06-30 | 2 | 2 | 0 | 1 | 15 | 1 | 2 | 1 | 0 | 0 | 1 | 2 |

### Non-parish rows, counted apart by designatedArea (PULL 3)

- Apache Choctaw (TDSA): 2
- Chitimacha Indian Reservation: 2
- Clifton Choctaw (TDSA): 2
- Coushatta Indian Reservation: 3
- Jena Band of Choctaw (TDSA): 2
- Statewide: 1
- Tunica-Biloxi Indian Reservation: 2
- United Houma Nation (TDSA): 2

## Top 15 parishes by DR declarations (PULL 3; ties by parish name)

| Rank | Parish | DR declarations | Total declarations | Latest |
|---|---|---|---|---|
| 1 | Lafourche | 24 | 43 | 2026-06-30 |
| 2 | St. Charles | 23 | 42 | 2026-06-30 |
| 3 | Livingston | 22 | 40 | 2026-01-24 |
| 4 | Assumption | 21 | 40 | 2026-01-24 |
| 5 | Jefferson | 21 | 40 | 2026-01-24 |
| 6 | St. Martin | 21 | 41 | 2026-01-24 |
| 7 | Terrebonne | 21 | 42 | 2026-06-30 |
| 8 | West Feliciana | 20 | 39 | 2026-01-24 |
| 9 | Ascension | 19 | 37 | 2026-01-24 |
| 10 | East Baton Rouge | 19 | 37 | 2026-01-24 |
| 11 | Iberville | 19 | 37 | 2026-01-24 |
| 12 | Orleans | 19 | 38 | 2026-01-24 |
| 13 | Plaquemines | 19 | 38 | 2026-01-24 |
| 14 | St. Bernard | 19 | 38 | 2026-01-24 |
| 15 | St. Mary | 19 | 41 | 2026-01-24 |

## Distinct DR disasterNumbers per fiscal year (PULL 3)

Fiscal year is taken from declarationDate: 1 October to 30 September. Years with no DR declarations show 0.

| Fiscal year | Distinct DR disasterNumbers |
|---|---|
| FY2000 | 1 |
| FY2001 | 2 |
| FY2002 | 1 |
| FY2003 | 1 |
| FY2004 | 2 |
| FY2005 | 3 |
| FY2006 | 0 |
| FY2007 | 2 |
| FY2008 | 2 |
| FY2009 | 0 |
| FY2010 | 1 |
| FY2011 | 1 |
| FY2012 | 2 |
| FY2013 | 1 |
| FY2014 | 0 |
| FY2015 | 1 |
| FY2016 | 2 |
| FY2017 | 1 |
| FY2018 | 1 |
| FY2019 | 3 |
| FY2020 | 2 |
| FY2021 | 5 |
| FY2022 | 0 |
| FY2023 | 0 |
| FY2024 | 1 |
| FY2025 | 0 |
| FY2026 | 2 |

## DisasterNumbers open a month or longer (PULL 3)

Distinct disasterNumbers whose latest incidentEndDate is on or after the same day of the next month after their earliest incidentBeginDate (a day that month lacks: its last day). DisasterNumbers with no end date are listed as open; PULL 3 has none.

1603, 1607, 1792, 3212, 3260, 3295, 3322, 3376, 3413, 3459, 3522, 3600, 4015, 4228, 4263, 4462, 4484, 5482, 5484, 5485, 5486

Open (no incidentEndDate): none.

## Changes — PULL 2 vs PULL 1

Matched by key column id. Changes columns: all columns after id.

No change. PULL 1 returned 2174 rows and PULL 2 returned 2174 rows. New (key only in the later pull): 0. Gone (key only in the earlier pull): 0. Changed (same key, a Changes column differs): 0. Later row count 2174 = earlier 2174 + 0 new − 0 gone. Both CSVs share SHA-256 6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599 (verified byte-identical with sha256sum and cmp).

## Changes — PULL 3 vs PULL 2

Matched by key column id. Changes columns: all columns after id.

No change. PULL 2 returned 2174 rows and PULL 3 returned 2174 rows. New (key only in the later pull): 0. Gone (key only in the earlier pull): 0. Changed (same key, a Changes column differs): 0. Later row count 2174 = earlier 2174 + 0 new − 0 gone. Both CSVs share SHA-256 6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599 (verified byte-identical with sha256sum and cmp).

## PROOF

One line per request (full request, UTC time, HTTP status), then under each pull its first response's Date header line copied exactly (the pull's source time), then each response's metadata object verbatim, then — for the last good pull, PULL 3 — the DR rows of the top-ranked parish (Lafourche) as returned, one per line.

### PROOF — PULL 1

```
PULL 1 — OpenFEMA DisasterDeclarationsSummaries, $filter=state eq 'LA' and fyDeclared ge 2000, $inlinecount=allpages, $select=id,femaDeclarationString,disasterNumber,declarationType,incidentType,declarationTitle,designatedArea,fipsCountyCode,declarationDate,incidentBeginDate,incidentEndDate, $top=1000, $skip paged.
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0 | UTC time: 2026-11-21 21:34:03 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000 | UTC time: 2026-11-21 21:34:06 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000 | UTC time: 2026-11-21 21:34:09 UTC | HTTP status: 200
First response Date header (source time of PULL 1):
Date: Sat, 21 Nov 2026 21:34:06 GMT
Metadata count ($inlinecount=allpages): 2174 on every page (1000 + 1000 + 174 rows).
```

### PULL 1 response 1 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-21T21:34:06.518Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 0,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0",
  "version": "v2"
}
```

### PULL 1 response 2 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-21T21:34:09.087Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 1000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000",
  "version": "v2"
}
```

### PULL 1 response 3 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-21T21:34:11.310Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 2000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000",
  "version": "v2"
}
```

### PROOF — PULL 2

```
PULL 2 — OpenFEMA DisasterDeclarationsSummaries, $filter=state eq 'LA' and fyDeclared ge 2000, $inlinecount=allpages, $select=id,femaDeclarationString,disasterNumber,declarationType,incidentType,declarationTitle,designatedArea,fipsCountyCode,declarationDate,incidentBeginDate,incidentEndDate, $top=1000, $skip paged.
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0 | UTC time: 2026-11-22 21:41:02 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000 | UTC time: 2026-11-22 21:41:04 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000 | UTC time: 2026-11-22 21:41:06 UTC | HTTP status: 200
First response Date header (source time of PULL 2):
Date: Sun, 22 Nov 2026 21:41:05 GMT
Metadata count ($inlinecount=allpages): 2174 on every page (1000 + 1000 + 174 rows).
```

### PULL 2 response 1 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-22T21:41:04.672Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 0,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0",
  "version": "v2"
}
```

### PULL 2 response 2 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-22T21:41:06.393Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 1000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000",
  "version": "v2"
}
```

### PULL 2 response 3 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-22T21:41:08.321Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 2000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000",
  "version": "v2"
}
```

### PROOF — PULL 3

```
PULL 3 — OpenFEMA DisasterDeclarationsSummaries, $filter=state eq 'LA' and fyDeclared ge 2000, $inlinecount=allpages, $select=id,femaDeclarationString,disasterNumber,declarationType,incidentType,declarationTitle,designatedArea,fipsCountyCode,declarationDate,incidentBeginDate,incidentEndDate, $top=1000, $skip paged.
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0 | UTC time: 2026-11-23 21:44:42 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000 | UTC time: 2026-11-23 21:44:44 UTC | HTTP status: 200
Request: https://www.fema.gov/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000 | UTC time: 2026-11-23 21:44:46 UTC | HTTP status: 200
First response Date header (source time of PULL 3):
Date: Mon, 23 Nov 2026 21:44:45 GMT
Metadata count ($inlinecount=allpages): 2174 on every page (1000 + 1000 + 174 rows).
```

### PULL 3 response 1 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-23T21:44:44.661Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 0,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=0",
  "version": "v2"
}
```

### PULL 3 response 2 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-23T21:44:46.426Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 1000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=1000",
  "version": "v2"
}
```

### PULL 3 response 3 metadata (verbatim)

```json
{
  "count": 2174,
  "entityname": "DisasterDeclarationsSummaries",
  "filter": "state eq 'LA' and fyDeclared ge 2000",
  "format": "json",
  "metadata": true,
  "orderby": "",
  "rundate": "2026-11-23T21:44:48.797Z",
  "select": "id, femaDeclarationString, disasterNumber, declarationType, incidentType, declarationTitle, designatedArea, fipsCountyCode, declarationDate, incidentBeginDate, incidentEndDate",
  "skip": 2000,
  "top": 1000,
  "url": "/api/open/v2/DisasterDeclarationsSummaries?%24filter=state+eq+%27LA%27+and+fyDeclared+ge+2000&%24inlinecount=allpages&%24select=id%2CfemaDeclarationString%2CdisasterNumber%2CdeclarationType%2CincidentType%2CdeclarationTitle%2CdesignatedArea%2CfipsCountyCode%2CdeclarationDate%2CincidentBeginDate%2CincidentEndDate&%24top=1000&%24skip=2000",
  "version": "v2"
}
```

### PULL 3 — DR rows of the top-ranked parish (Lafourche), as returned, one per line

```
{"id": "d98ea675-013c-405e-9d2b-2f3d568041c7", "femaDeclarationString": "DR-4927-LA", "disasterNumber": 4927, "declarationType": "DR", "incidentType": "Tropical Storm", "declarationTitle": "TROPICAL STORM ARTHUR", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2026-06-30T00:00:00.000Z", "incidentBeginDate": "2026-06-17T00:00:00.000Z", "incidentEndDate": "2026-06-24T00:00:00.000Z"}
{"id": "3b850f29-f5ba-4626-a11b-f59c7fdbb5f4", "femaDeclarationString": "DR-4817-LA", "disasterNumber": 4817, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE FRANCINE", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2024-09-16T00:00:00.000Z", "incidentBeginDate": "2024-09-09T00:00:00.000Z", "incidentEndDate": "2024-09-12T00:00:00.000Z"}
{"id": "42999a51-b504-41dc-aa56-65d337c4ed71", "femaDeclarationString": "DR-4611-LA", "disasterNumber": 4611, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE IDA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2021-08-29T00:00:00.000Z", "incidentBeginDate": "2021-08-26T00:00:00.000Z", "incidentEndDate": "2021-09-03T00:00:00.000Z"}
{"id": "16249617-b294-4e37-aa74-19a45c132b56", "femaDeclarationString": "DR-4606-LA", "disasterNumber": 4606, "declarationType": "DR", "incidentType": "Flood", "declarationTitle": "SEVERE STORMS, TORNADOES, AND FLOODING", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2021-06-02T00:00:00.000Z", "incidentBeginDate": "2021-05-17T00:00:00.000Z", "incidentEndDate": "2021-05-21T00:00:00.000Z"}
{"id": "fee1c275-b2d9-4d39-aee2-4d4051402992", "femaDeclarationString": "DR-4590-LA", "disasterNumber": 4590, "declarationType": "DR", "incidentType": "Severe Ice Storm", "declarationTitle": "SEVERE WINTER STORMS", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2021-03-09T00:00:00.000Z", "incidentBeginDate": "2021-02-11T00:00:00.000Z", "incidentEndDate": "2021-02-19T00:00:00.000Z"}
{"id": "05980d1b-b4da-4183-823d-6f1d1916c15b", "femaDeclarationString": "DR-4577-LA", "disasterNumber": 4577, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE ZETA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2021-01-12T00:00:00.000Z", "incidentBeginDate": "2020-10-26T00:00:00.000Z", "incidentEndDate": "2020-10-29T00:00:00.000Z"}
{"id": "d9782f07-4aed-4513-8c2b-fb4d4adfb667", "femaDeclarationString": "DR-4570-LA", "disasterNumber": 4570, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE DELTA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2020-10-16T00:00:00.000Z", "incidentBeginDate": "2020-10-06T00:00:00.000Z", "incidentEndDate": "2020-10-10T00:00:00.000Z"}
{"id": "dc44ef35-4319-4dac-81ec-fa91bcb272f8", "femaDeclarationString": "DR-4559-LA", "disasterNumber": 4559, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE LAURA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2020-08-28T00:00:00.000Z", "incidentBeginDate": "2020-08-22T00:00:00.000Z", "incidentEndDate": "2020-08-27T00:00:00.000Z"}
{"id": "dead875c-9370-4fd2-b2d4-879e6bfe7c4a", "femaDeclarationString": "DR-4484-LA", "disasterNumber": 4484, "declarationType": "DR", "incidentType": "Biological", "declarationTitle": "COVID-19 PANDEMIC", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2020-03-24T00:00:00.000Z", "incidentBeginDate": "2020-01-20T00:00:00.000Z", "incidentEndDate": "2023-05-11T00:00:00.000Z"}
{"id": "71b28036-b18d-4511-8f67-d89ab6d50304", "femaDeclarationString": "DR-4458-LA", "disasterNumber": 4458, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE BARRY", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2019-08-27T00:00:00.000Z", "incidentBeginDate": "2019-07-10T00:00:00.000Z", "incidentEndDate": "2019-07-15T00:00:00.000Z"}
{"id": "bdadbce6-8b7c-4631-81ab-e4023baccaf7", "femaDeclarationString": "DR-4345-LA", "disasterNumber": 4345, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "TROPICAL STORM HARVEY", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2017-10-16T00:00:00.000Z", "incidentBeginDate": "2017-08-28T00:00:00.000Z", "incidentEndDate": "2017-09-10T00:00:00.000Z"}
{"id": "75dbadcb-7fde-4d6e-9dad-6535782bc75f", "femaDeclarationString": "DR-4263-LA", "disasterNumber": 4263, "declarationType": "DR", "incidentType": "Flood", "declarationTitle": "SEVERE STORMS AND FLOODING", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2016-03-13T00:00:00.000Z", "incidentBeginDate": "2016-03-08T00:00:00.000Z", "incidentEndDate": "2016-04-08T00:00:00.000Z"}
{"id": "d314c845-733b-4335-ad9d-eccc79df4ce4", "femaDeclarationString": "DR-4080-LA", "disasterNumber": 4080, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE ISAAC", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2012-08-29T00:00:00.000Z", "incidentBeginDate": "2012-08-26T00:00:00.000Z", "incidentEndDate": "2012-09-10T00:00:00.000Z"}
{"id": "62123169-aa4b-40eb-98e5-1376ea4c2f43", "femaDeclarationString": "DR-4041-LA", "disasterNumber": 4041, "declarationType": "DR", "incidentType": "Coastal Storm", "declarationTitle": "TROPICAL STORM LEE", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2011-10-28T00:00:00.000Z", "incidentBeginDate": "2011-09-01T00:00:00.000Z", "incidentEndDate": "2011-09-05T00:00:00.000Z"}
{"id": "6b5113b2-f346-4fba-9ccd-308a50ad6035", "femaDeclarationString": "DR-4015-LA", "disasterNumber": 4015, "declarationType": "DR", "incidentType": "Flood", "declarationTitle": "FLOODING", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2011-08-18T00:00:00.000Z", "incidentBeginDate": "2011-04-25T00:00:00.000Z", "incidentEndDate": "2011-07-07T00:00:00.000Z"}
{"id": "c39b95cf-80b6-439a-a019-799e9d22e274", "femaDeclarationString": "DR-1792-LA", "disasterNumber": 1792, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE IKE", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2008-09-13T00:00:00.000Z", "incidentBeginDate": "2008-09-11T00:00:00.000Z", "incidentEndDate": "2008-11-07T00:00:00.000Z"}
{"id": "873136f9-e0c1-49e6-b1fa-d60356f3914d", "femaDeclarationString": "DR-1786-LA", "disasterNumber": 1786, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE GUSTAV", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2008-09-02T00:00:00.000Z", "incidentBeginDate": "2008-09-01T00:00:00.000Z", "incidentEndDate": "2008-09-11T00:00:00.000Z"}
{"id": "0b0204ad-7e0d-49d7-85f0-36e2b563d6f6", "femaDeclarationString": "DR-1607-LA", "disasterNumber": 1607, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE RITA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2005-09-24T00:00:00.000Z", "incidentBeginDate": "2005-09-23T00:00:00.000Z", "incidentEndDate": "2005-11-01T00:00:00.000Z"}
{"id": "62535a11-ed13-4b78-ab84-956d697760ce", "femaDeclarationString": "DR-1603-LA", "disasterNumber": 1603, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE KATRINA", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2005-08-29T00:00:00.000Z", "incidentBeginDate": "2005-08-29T00:00:00.000Z", "incidentEndDate": "2005-11-01T00:00:00.000Z"}
{"id": "74ef6208-2e3b-4d26-80fe-735a7942e3e9", "femaDeclarationString": "DR-1601-LA", "disasterNumber": 1601, "declarationType": "DR", "incidentType": "Severe Storm", "declarationTitle": "TROPICAL STORM CINDY", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2005-08-23T00:00:00.000Z", "incidentBeginDate": "2005-07-05T00:00:00.000Z", "incidentEndDate": "2005-07-06T00:00:00.000Z"}
{"id": "b1c163e3-9e19-4e24-b014-71ceb4d3fc8a", "femaDeclarationString": "DR-1548-LA", "disasterNumber": 1548, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE IVAN", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2004-09-15T00:00:00.000Z", "incidentBeginDate": "2004-09-13T00:00:00.000Z", "incidentEndDate": "2004-09-26T00:00:00.000Z"}
{"id": "e14b1bdb-fc24-438c-b6ef-826fd6ff9c14", "femaDeclarationString": "DR-1437-LA", "disasterNumber": 1437, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "HURRICANE LILI", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2002-10-03T00:00:00.000Z", "incidentBeginDate": "2002-10-01T00:00:00.000Z", "incidentEndDate": "2002-10-16T00:00:00.000Z"}
{"id": "3a3fb785-ace3-4a52-81cc-4a6369ad346e", "femaDeclarationString": "DR-1435-LA", "disasterNumber": 1435, "declarationType": "DR", "incidentType": "Hurricane", "declarationTitle": "TROPICAL STORM ISIDORE", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2002-09-27T00:00:00.000Z", "incidentBeginDate": "2002-09-21T00:00:00.000Z", "incidentEndDate": "2002-10-01T00:00:00.000Z"}
{"id": "25619c2f-b514-41f4-a445-c5b44b938dfa", "femaDeclarationString": "DR-1380-LA", "disasterNumber": 1380, "declarationType": "DR", "incidentType": "Coastal Storm", "declarationTitle": "TROPICAL STORM ALLISON", "designatedArea": "Lafourche (Parish)", "fipsCountyCode": "057", "declarationDate": "2001-06-11T00:00:00.000Z", "incidentBeginDate": "2001-06-05T00:00:00.000Z", "incidentEndDate": "2001-06-22T00:00:00.000Z"}
```

```synmerco-data
6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599 la-disasters-pull1.csv
6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599 la-disasters-pull2.csv
6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599 la-disasters-pull3.csv
```

<!-- FINAL — regenerated from the last good pull (PULL 3). All three pull CSVs are byte-identical (SHA-256 6568f428d27e0c3434a8ee7bde378a89a67269a64d4b21f658e340a072118599). Do not edit after submit; the SHA-256 of this file is the proofHash. -->