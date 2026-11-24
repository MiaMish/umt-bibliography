# Validation and provenance notes

Snapshot checked: 24 November 2026, following the source-reference and work-foreign-key revision. Structural and referential checks were rerun on all six published summary tables. Bibliographical verification for this revision was limited to the already identified 1944 digital witness; no broader source or book reinspection was undertaken.

## Structural checks

- All six CSVs decode strictly as UTF-8, have unique header names, consistent row widths and parse with standard CSV quoting.
- Row counts: works 42; editions 180; contributors 46; translations 14; collections 20; digital access 42.
- Work, publication, contributor and translation identifiers are nonempty and unique. Work titles and collection institution names are unique in this snapshot.
- All 180 edition rows and 14 translation rows have nonempty `work_id` foreign keys resolving to `works.work_id`. Their retained `title` and `original_title` values match the linked work titles. IDs were assigned from the existing unique title matches, without changing row order or adding records. All contributor work references resolve. Contributor title counts equal their assigned work-link counts. Digital summaries cover all work IDs exactly once, with matching titles.
- Work and edition years and populated impression years are four-digit integers. Collection counts and digital-object counts are nonnegative integers. No empty edition/translation/access status occurs; all labels are documented in the data dictionary.
- Every work, edition and translation has a source URL. Every collection has an example-record URL. Source links were retained; this release does not certify that every link is live or that every source supports every cell.

## Missing values and unresolved evidence

| Table | Blank fields (count) |
| --- | --- |
| works | `series_no` 8; optional `note` 30 |
| editions | `impression` 166; `designation` 61; `pages` 13; optional `note` 107 |
| contributors | `dates` 28; `work_ids` 11; `source` 28 |
| translations | `date` 2; `translator` 2; `publisher` 1 |
| collections | None |
| digital_access | `inspected_editions` 34; `best_item` 1; `pdf` 33 |

Blank notes can simply mean no additional qualification was recorded. Blank bibliographical fields remain unresolved or unrecorded. Ancillary contributors without work links are retained, rather than assigning uncertain relationships.

Edition status counts are 141 catalogue-supported provisional records, 12 with identifying pages inspected and 27 metadata leads. Translation status counts are seven catalogue-supported unchecked copies, two undated attestations, three contemporary notices and two leads. Digital-access counts are eight inspected open-PDF titles, one unverified open-PDF title, 32 restricted/untested titles and one title with no located digitization.

## Source correction verified

`E-AIT-SM-1944-3` now cites [Internet Archive item in.ernet.dli.2015.212078](https://archive.org/details/in.ernet.dli.2015.212078) instead of the 1949 scan. Existing images of PDF pages 4–5 were visually rechecked: the title page identifies *Statistical Mathematics*, A. C. Aitken, Oliver & Boyd, 1944; the facing publication history lists the third edition in 1944. This supports the work, year and third-edition identity. The existing `Identifying pages inspected` status is retained; no physical-copy inspection, textual collation or whole-book completeness is claimed.

Specific cautions retained without silently resolving the records:

- `E-AIT-SM-1942-2` continues to cite the later 1949 scan, potentially as publication-history evidence. It must not be treated as a matching-copy reference. This revision does not resolve that separate record.
- McCrea’s 1945 reprint, Aitken’s 1945/1946 discrepancy and Phillips’s eighth-/ninth-edition discrepancy are described in the README; no new edition identities have been inferred.
- An Open Library 1965 lead for *Vector spaces of finite dimension* coexists with the work roster’s 1966 first-publication candidate. The lead remains provisional.
- `E-RIN-SR-1966-2-imp1969` records edition year 1966 and impression year 1969. These are different bibliographical attributes, not an automatic inconsistency.
- Two known duplicate digital groups were consolidated in the recorded total of 17 digital objects. The public summary does not enumerate the full object manifest, so deduplication cannot be independently reproduced from these six tables alone.
- Collection totals are selected retrieved-record summaries, with only one example URL each. They cannot be reconstructed as a full holdings census from this repository.

## Source attribution and rights scope

This repository publishes a selective bibliographical compilation: short factual descriptions, identifiers, pagination, responsibility statements, verification notes and source links. It includes no catalogue exports in full, descriptive essays copied from catalogues, book text, scans, cover images or OCR. Linked materials are not redistributed. The original selection, arrangement and documentation are offered under CC BY 4.0 to the extent of the author’s rights. Externally sourced metadata is not blanket-relicensed.

Source terms reviewed for this release:

- **NII / CiNii Books:** [NII’s copyright policy](https://support.nii.ac.jp/en/cinii/copyright) releases NACSIS-CAT records under CC BY 4.0. Credit: National Institute of Informatics (NII), NACSIS-CAT via CiNii Books. The published tables adapt and abbreviate bibliographical facts from those records. Proprietary BOOK/Nielsen enrichment is outside that licence; no such enrichment is intentionally reproduced here.
- **Abes / Sudoc:** [Abes’s metadata reuse policy](https://abes.fr/reseau-sudoc/reutiliser-les-donnees-sudoc/formats-de-donnees-disponibles/) provides metadata under the French Licence Ouverte / Open Licence, requiring source and retrieval-date attribution. Source: Agence bibliographique de l’Enseignement supérieur, Sudoc Public. Recorded Sudoc request logs give an access date of 8 November 2026. The summary tables omit individual retrieval timestamps and abbreviate and regroup the retrieved records.
- **Princeton University Library:** [PUL Open Dataset terms](https://catalog.princeton.edu/dataset) use CC0 for the specified open dataset, which excludes certain vendor-supplied and ReCAP partner records. The catalogue references here are not a claim that every referenced record belongs to that CC0 dataset. Credit Princeton University Library and the named holding institutions, including Columbia University Libraries, Harvard Library and New York Public Library, as applicable.
- **Open Library:** [Open Library’s data policy](https://openlibrary.org/help/faq/using) describes its catalogue as public-domain data and requests CC0 contributions. Bibliographical source URLs are retained.
- **Other institutions, digital libraries and biographical sources:** source URLs identify the factual references used. Their website content and linked facsimiles remain under their own terms. No independent right to redistribute those materials is asserted.

The selective factual references here do not establish that arbitrary third-party catalogue exports or substantial extractions may be republished. Any future addition of such records, enriched descriptions, images or facsimiles requires a separate rights review. The licence does not override provider terms or grant rights the author does not hold.

## Public-content review

Only the six selected CSVs, README, data dictionary, validation notes, citation metadata, official licence text and ignore rules are included. Collection grouping and the Princeton reader-access note were generalized. This revision corrects the 1944 *Statistical mathematics* source URL and adds work foreign keys to editions and translations; other existing data values and row counts are unchanged. No research notes, working directories, downloaded objects, credentials, private contact details or absolute local paths are included. The commit uses GitHub’s public no-reply address rather than a private email address.
