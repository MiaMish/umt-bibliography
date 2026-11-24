# University Mathematical Texts (1939–1972): A Preliminary Bibliographical Inventory

A working bibliographical inventory of the University Mathematical Texts (UMT), a series of mathematical textbooks published by Oliver & Boyd, initially edited by A. C. Aitken and D. E. Rutherford. It brings together titles, publication records, contributors, translations, selected library collections and digital-access references to support bibliographical research and the verification of individual records.

**This is a working inventory, not an exhaustive or definitive bibliography.** The dates 1939–1972 describe the currently identified first-publication roster. Selected later reissues are also recorded.

Current release: **24 November 2026** (initial repository snapshot). Access and verification statements reflect the underlying compilation, documented by 8 November 2026; they have not been systematically rechecked for this release.

## Corpus and files

Counts calculated directly from the six CSVs, excluding headers:

| File | Rows | Purpose |
| --- | ---: | --- |
| [works.csv](works.csv) | 42 | Separately titled volumes, with first-publication candidates, attested series numbers, authors and subjects. |
| [editions.csv](editions.csv) | 180 | Provisional edition, impression and issue groupings, including selected later reissues (record years 1939–2020). |
| [contributors.csv](contributors.csv) | 46 | Partial author, editor and translator authorities, with selected biographical references. |
| [translations.csv](translations.csv) | 14 | Translations and leads, with differing levels of verification. |
| [collections.csv](collections.csv) | 20 | Selected institutions and counts from retrieved holdings records; not a worldwide census. |
| [digital_access.csv](digital_access.csv) | 42 | One digital-access summary per titled volume, with external item and PDF links where recorded. |

Of the 42 titled volumes, 22 have first-publication candidates before 1960. Noble’s two separately titled *Numerical methods* parts count separately; grouping these yields 41 parent works. Eight series numbers remain unverified.

The 180 publication records comprise 141 labelled `Catalogue-supported; provisional`, 12 `Identifying pages inspected`, and 27 `Metadata lead only`. They do not establish 180 distinct textual revisions or physically verified editions. The translation table contains nine Spanish, four German and one Italian records or leads.

Digital-access summaries comprise eight titles labelled `Open PDF; identifying pages inspected`, one `Open PDF; edition not verified`, 32 `Restricted scans / untested leads`, and one `No digitized copy located`. The recorded `downloaded_objects` counts sum to 17 after known duplicate groups were consolidated. These are digital objects, not 17 editions. No downloaded files are distributed here.

## Identifiers and bibliographical units

`work_id` identifies a separately titled volume (`W-…`); `edition_id` identifies a provisional publication grouping (`E-…`); `contributor_id` identifies a person (`A-…`); and `translation_id` identifies a translation record or lead (`T-…`). Treat identifiers as opaque labels, not independent bibliographical evidence. Their suffixes can reflect provisional interpretations.

`digital_access.work_id` and the semicolon-separated `contributors.work_ids` refer to `works.work_id`. The editions table joins to works by exact `title`; translations join by exact `original_title`. These title joins currently resolve uniquely, but should be reviewed whenever a title changes. Contributor names in other tables are text, not foreign keys. Collections are aggregate summaries without copy identifiers or edition-level links.

A **work** is distinct from an **edition** (a publication version), an **impression** (a printing), an **issue** (a distribution or imprint variant), a **physical copy** (an individual exemplar), and a **digital object** (a scan or file representing an exemplar). Catalogue edition wording is retained without assuming textual revision. Several catalogue records may describe one publication; several digital objects may reproduce one copy. The summary tables do not provide a complete copy census or a fully normalized model of these relationships.

See [DATA_DICTIONARY.md](DATA_DICTIONARY.md) for every column and the status vocabulary.

## Sources and provenance

The compilation combines contemporary Oliver & Boyd advertisements, inspected identifying pages of digitized books, institutional catalogues and digital-library metadata. Principal discovery and verification sources include:

- [Princeton University Library catalogue](https://catalog.princeton.edu/), including separately identified ReCAP partner records. A partner record does not establish a Princeton-owned copy.
- [CiNii Books, provided by the National Institute of Informatics (NII)](https://ci.nii.ac.jp/books/), including the [UMT series record](https://ci.nii.ac.jp/ncid/BA03774621?l=en), and [Sudoc, Agence bibliographique de l’Enseignement supérieur (Abes)](https://www.sudoc.fr/), for bibliography and holdings.
- [Open Library](https://openlibrary.org/), [Internet Archive](https://archive.org/) (including Digital Library of India scans), and [HathiTrust](https://www.hathitrust.org/), for publication and digital-copy discovery. Discovery metadata and search-only records do not establish full-text access.
- [Oliver & Boyd advertisement, May 1961, printed p. 58](https://www.oemg.ac.at/IMN/imn067.pdf), for series and editorial evidence. This is a selection, not a terminal publisher list.
- Contemporary notices and historical bibliographical evidence linked from translation rows; selected biographical authorities linked from contributor rows.

Each work, publication and translation row retains a source URL; collection rows retain an example record. These concise references are not an exhaustive list of witnesses, and a cited scan may support an earlier date through its publication history. Contributor provenance is incomplete: 28 rows lack an individual source URL. For linked authors, work-level references provide additional bibliographical context, but do not independently establish all biographical or editorial claims.

The published CSVs retain the compilation’s bibliographical values and status labels. Collection group labels and the Princeton reader-access note have been generalized for public use. No new bibliographical facts have been supplied to fill blanks.

## Verification and access

`Catalogue-supported; provisional` means a grouping is supported by a catalogue or comparable publication-history reference, without establishing inspection of a matching copy. `Identifying pages inspected` records a check of title or publication-history pages in a digital witness; it does not mean physical inspection, complete textual collation or verification of every leaf. `Metadata lead only` requires further verification. Translation statuses distinguish catalogue support, a contemporary announcement, an attested but undated issue, and a lead awaiting item verification.

An `Open PDF` label records access at the time of compilation, not a rights determination or a promise of continuing availability. Restricted scans and untested leads remain distinct from verified open downloads. `No digitized copy located` reports a search outcome, not proof that none exists. **Publicly accessible digitization does not establish public-domain status or permission to redistribute.**

## Known limitations

- A final publisher list is missing; roster completeness, eight series numbers and some first-publication candidates remain provisional.
- Publication groupings may need splitting or merging after inspection. Original pagination, brackets, approximate dates and conflicting catalogue wording are retained.
- McCrea’s 1945 record is a reprint of the 1942 publication. Aitken’s fourth revised *Statistical mathematics* is dated 1945 by a later history; an OCR derivative gives 1946. Phillips’s inspected 1961 witness is an impression of the 1957 eighth edition, despite a ninth-edition catalogue description.
- The 1944 *Statistical mathematics* record links to a 1949 scan. Its status is retained from the compilation, but the link alone does not identify a matching 1944 copy; the digital-access summary separately identifies the 1944 witness. See [VALIDATION.md](VALIDATION.md).
- Whole-book completeness has not been checked leaf by leaf. Known digital duplicates have been consolidated, but other duplicates may remain.
- Holdings counts describe retrieved records, not complete local collections, current availability or reader eligibility. Translation and contributor coverage is partial. Blank fields mean unresolved or unrecorded information; they must not be converted into inferred values.

## Suggested citation

Joskowicz, Mia. 2026. *University Mathematical Texts (1939–1972): A Preliminary Bibliographical Inventory*. Snapshot of 24 November 2026. https://github.com/MiaMish/umt-bibliography. Cite the commit hash used when reproducibility matters.

Machine-readable citation metadata is provided in [CITATION.cff](CITATION.cff). Corrections with supporting references are welcome through repository issues.

## Licence

© 2026 Mia Joskowicz.

The original bibliographical compilation and accompanying documentation are licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) licence, to the extent that the author holds the relevant rights.

Third-party materials and externally sourced metadata remain subject to their respective rights and terms of use.

Users are kindly requested to cite this repository when using the dataset in academic research.

The official [CC BY 4.0 legal text](LICENSE) is included. This licence does not place new restrictions on facts or material already in the public domain, and does not license the linked books, facsimiles, websites or third-party catalogue records. Source attribution and rights notes are recorded in [VALIDATION.md](VALIDATION.md).
