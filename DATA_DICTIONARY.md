# Data dictionary

All tables are UTF-8, comma-separated CSVs with a header row. Quoted fields may contain commas. Values are text unless described as counts or years below. Blank cells mean unresolved or unrecorded information, not zero, absence or a negative finding. Brackets, question marks and catalogue wording are intentional. Semicolons separate lists in selected fields; they are not CSV delimiters.

## works.csv

One row per separately titled volume. Noble’s two parts have separate work IDs.

| Column | Meaning |
| --- | --- |
| `work_id` | Unique local work identifier. |
| `year` | Four-digit candidate first-publication year; does not imply inspection of the first issue. |
| `series_no` | Series number only where explicitly attested; blank when unverified. |
| `title` | Inventory title; unique in this snapshot. Retained title fields in publication and translation records are checked against this value; joins use `work_id`. |
| `author` | Author names; multiple names separated by semicolons. |
| `subject` | Concise descriptive subject terms separated by semicolons. |
| `source` | Selected bibliographical reference URL. |
| `note` | Qualifications concerning numbering, multipart works or translated origins. |

## editions.csv

One row per provisional edition, impression or issue grouping. These rows are not a census of physical copies, and edition designations do not prove textual differences.

| Column | Meaning |
| --- | --- |
| `edition_id` | Unique local publication-record identifier. Suffixes such as `US`, `imp…`, `unspecified` or `reissue` preserve provisional distinctions. |
| `work_id` | Required foreign key to `works.work_id`; identifies the work associated with this publication grouping. Repeats across publication records for the same work. |
| `title` | Retained inventory title; matches `works.title` for the linked `work_id`. |
| `year` | Four-digit year assigned to the publication grouping; can differ from the impression year. Includes later reissues. |
| `impression` | Four-digit printing year where separately recorded; 14 populated cells. A blank does not establish that a record is a new edition. |
| `designation` | Selected edition or printing wording, including brackets and qualifications; blank if unstated or unresolved. |
| `pages` | Pagination or extent as recorded, with catalogue punctuation and occasional qualifications; not a normalized leaf count. |
| `status` | Verification label defined below. |
| `source` | Selected catalogue, metadata or digital-witness URL. A later witness can support a publication-history statement about an earlier issue. |
| `note` | Issue, reissue, dating or other qualifications. |

## contributors.csv

Partial person authorities, not a definitive biographical register.

| Column | Meaning |
| --- | --- |
| `contributor_id` | Unique local person identifier. |
| `name` | Recorded personal name; some names remain abbreviated. |
| `dates` | Recorded life dates, when available; not editorial tenure dates. |
| `roles` | Semicolon-separated role descriptions and unresolved qualifications. `dates unresolved` in an editorial-role entry may concern tenure even if life dates are present. |
| `umt_titles` | Integer count of linked titled volumes; zero for ancillary contributors without assigned work links, not proof of no contribution. |
| `work_ids` | Semicolon-separated references to `works.work_id`; blank where unassigned. |
| `source` | Selected person-level reference URL, where recorded. Missing URLs are a provenance limitation. |

## translations.csv

One row per translation record or lead, including distinct issues and undated attestations. No complete translated facsimile has been established in this compilation.

| Column | Meaning |
| --- | --- |
| `translation_id` | Unique local record identifier; source-based suffixes are not a verification guarantee. |
| `work_id` | Required foreign key to `works.work_id`; identifies the original work associated with this translation record or lead. Repeats across translations of the same work. |
| `original_title` | Retained original inventory title; matches `works.title` for the linked `work_id`. |
| `translated_title` | Recorded translated title, retaining source spelling. |
| `language` | Language of the translation or lead. |
| `date` | Free-text date or uncertainty, including brackets, `c`, `s. f.` (undated) and announcement bounds. Do not parse all values as publication years. |
| `translator` | Recorded translator or responsibility statement; may include catalogue transcription such as `al cuidado de`. |
| `publisher` | Recorded publisher, where available. |
| `status` | Verification label defined below. |
| `source` | Selected catalogue, contemporary notice or bibliographical evidence URL; a lead may point to an authority record rather than an item. |

## collections.csv

Selected institutional summaries. Institution names are unique in this snapshot, but no stable collection IDs are assigned.

| Column | Meaning |
| --- | --- |
| `group` | Broad geographical grouping for presentation. |
| `institution` | Institution or named subcollection. |
| `country` | Country label. |
| `titles` | Integer count of inventory titles found in retrieved holdings records. Counts overlap across institutions and must not be summed as unique titles. |
| `edition_records` | Integer count of publication/holding groupings retrieved for that institution, not proven distinct editions or physical-copy counts. |
| `access_note` | Recorded consultation or loan qualification; current conditions require confirmation. |
| `example_record` | One illustrative source URL, not a complete evidential list for the aggregate count. |

## digital_access.csv

One summary per `work_id`; the table does not enumerate every digital object.

| Column | Meaning |
| --- | --- |
| `work_id` | Unique reference to `works.work_id`. |
| `title` | Matching inventory title. |
| `access` | Access/verification label defined below. |
| `downloaded_objects` | Nonnegative integer count of digital objects retained after known duplicate groups were consolidated. This is a recorded acquisition count, not a count of editions or a current access guarantee. |
| `inspected_editions` | Free-text list of dates and identifying-page wording for inspected witnesses, separated by semicolons. Some entries contain semicolons within their descriptions; this field is not a normalized relation. |
| `best_item` | Selected external item/landing-page URL; restricted and untested leads may be included. |
| `pdf` | Selected external PDF URL when recorded; no file is bundled and no redistribution right is implied. |
| `note` | Completeness or access qualification. |

## Status vocabulary

These labels report the compilation’s recorded evidence, not a fresh audit of the books for this repository release.

| Table/field | Exact label | Meaning |
| --- | --- | --- |
| editions/status | `Catalogue-supported; provisional` | Catalogue or comparable publication-history support; matching-copy inspection not established by the label. |
| editions/status | `Identifying pages inspected` | Title/history pages of a digital witness checked; no physical inspection, mathematical collation or full leaf check implied. |
| editions/status | `Metadata lead only` | Discovery metadata requiring further verification. |
| translations/status | `Catalogue-supported; copy unchecked` | Catalogue support; translated copy not inspected. |
| translations/status | `Translation attested; issue undated` | Bibliographical attestation without an established issue date. |
| translations/status | `Contemporary notice; copy unchecked` | Contemporary announcement; copy and precise publication details unchecked. |
| translations/status | `Lead; item verification needed` | Tentative lead requiring item-level verification. |
| digital_access/access | `Open PDF; identifying pages inspected` | Public PDF access recorded and identifying pages checked; whole-book completeness uncollated. |
| digital_access/access | `Open PDF; edition not verified` | Public PDF access recorded, but publication identity unverified. |
| digital_access/access | `Restricted scans / untested leads` | Restricted material or discovery leads; full page-image access not established. |
| digital_access/access | `No digitized copy located` | No digital copy found in the searches represented; not evidence of absence. |

`Local access conditions unverified.` and other collection access notes concern physical consultation, not digital access or copyright. Works, contributors and collections have no uniform row-level verification field; no status should be inferred from its absence.
