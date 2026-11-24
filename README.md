# University Mathematical Texts (1939–1972)

## A Bibliographical Inventory

The *University Mathematical Texts* (UMT) series, published by Oliver & Boyd and initially edited by A. C. Aitken and D. E. Rutherford, is a series of short, affordable mathematical textbooks intended primarily for university teaching. Between 1939 and 1972, it expanded to more than forty titles covering subjects including algebra, analysis, geometry, statistics, mathematical physics and numerical methods. Many of the series' volumes appeared in successive editions, circulated internationally and were translated into other languages.

This repository includes bibliographical information on the series, its contributors, publication histories, translations, library holdings and digital availability. The inventory provides a starting point for tracing the development and circulation of the series and locating sources for comparative research on twentieth-century mathematical textbooks.

The inventory will be updated as further sources are identified and examined.

## The corpus

The current inventory includes 42 separately titled volumes and 180 publication records, including editions, impressions, issues and selected later reissues.

| File                                     | Records | Contents                                                                           |
|------------------------------------------|--------:|------------------------------------------------------------------------------------|
| [works.csv](works.csv)                   |      42 | Titles, authors, first-publication dates, series numbers and mathematical subjects |
| [editions.csv](editions.csv)             |     180 | Publication histories, including editions, impressions and issues                  |
| [contributors.csv](contributors.csv)     |      46 | Authors, editors, translators and biographical information                         |
| [translations.csv](translations.csv)     |      14 | Identified translations and bibliographical leads                                  |
| [collections.csv](collections.csv)       |      20 | Selected library collections and holdings information                              |
| [digital_access.csv](digital_access.csv) |      42 | Digital availability and links to external resources                               |

The two separately titled parts of Benjamin Noble's *Numerical Methods* are counted individually, yielding 42 volumes corresponding to 41 parent works. Of these volumes, 22 were first published, according to the available evidence, before 1960.

The publication records distinguish between different editions, impressions and issues where the available evidence permits. The number of records does not correspond to the number of distinct textual revisions.

## Library holdings and digital access

The inventory identifies substantial collections of UMT volumes, including holdings records for 39 titles at Princeton University Library and 37 at the Institut Henri Poincaré in Paris.

Digital-access information includes openly accessible facsimiles, restricted digitizations and further acquisition leads. The preliminary survey has identified and retrieved 17 distinct digital objects, with 12 editions identified through inspection of their title or publication-history pages.

Links to available resources are included in the relevant CSV files. No facsimiles are distributed through this repository.

## Sources

The inventory was assembled using contemporary publisher advertisements, institutional library catalogues, digital libraries and the identifying pages of digitized books.

Principal sources include:

- [CiNii Books](https://ci.nii.ac.jp/books/), including its [University Mathematical Texts series record](https://ci.nii.ac.jp/ncid/BA03774621?l=en)
- [Sudoc](https://www.sudoc.fr/)
- [Princeton University Library](https://catalog.princeton.edu/)
- [Internet Archive](https://archive.org/), including the Digital Library of India collections
- [Open Library](https://openlibrary.org/)
- [HathiTrust](https://www.hathitrust.org/)
- Contemporary Oliver & Boyd advertisements and other bibliographical sources

References to individual sources are included in the dataset, alongside information about the verification status of the records.

## Data structure and documentation

Each titled volume is assigned a unique `work_id`, which connects the bibliographical, publication, translation, contributor and digital-access records.

- [Data dictionary](DATA_DICTIONARY.md) — column definitions, identifiers, relationships between tables and verification categories.
- [Data Quality and Provenance](DATA_QUALITY.md) — data quality checks, bibliographical uncertainties and known limitations.

The inventory distinguishes catalogue-supported information from records verified through the inspection of identifying pages. Publication histories, contributor information, translations and holdings remain subject to further research and verification.

Library holdings and digital-access information reflect the results of the preliminary survey and do not necessarily indicate current availability.

## Citation

Joskowicz, Mia. 2026. *University Mathematical Texts (1939–1972): A Bibliographical Inventory*. GitHub. https://github.com/MiaMish/umt-bibliography.

For reproducibility, cite the relevant commit or release.

Machine-readable citation metadata is available in [CITATION.cff](CITATION.cff).

## Contributing

Corrections, additional records and references are welcome through GitHub issues, preferably accompanied by supporting bibliographical evidence.

## Licence

© 2026 Mia Joskowicz.

The original bibliographical compilation and accompanying documentation are licensed under the [Creative Commons Attribution 4.0 International licence (CC BY 4.0)](LICENSE), to the extent that the author holds the relevant rights.

Third-party materials and externally sourced metadata remain subject to their respective rights and terms of use. The licence does not extend to linked books or facsimiles.

*Last updated: 24 November 2026.*
