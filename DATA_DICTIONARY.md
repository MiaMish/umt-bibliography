# Data dictionary

All tables are UTF-8 encoded, comma-separated CSV files with a header row. Values are text unless otherwise specified. Semicolons separate lists in selected fields.

Blank fields indicate information that has not been recorded, has not yet been established or is not applicable. Brackets, question marks and qualified catalogue wording reflect bibliographical uncertainties.

## works.csv

One record per separately titled volume. The two parts of Benjamin Noble's *Numerical Methods* are assigned separate work identifiers.

| Column      | Description                                                |
|-------------|------------------------------------------------------------|
| `work_id`   | Unique work identifier.                                    |
| `year`      | Identified or provisional first-publication year.          |
| `series_no` | Series number, where explicitly attested.                  |
| `title`     | Title of the work as recorded in the inventory.            |
| `author`    | Author names, separated by semicolons where applicable.    |
| `subject`   | Descriptive subject terms, separated by semicolons.        |
| `source`    | Bibliographical reference URL.                             |
| `note`      | Additional bibliographical information and qualifications. |

## editions.csv

One record per identified or provisional edition, impression or issue grouping. Publication records do not necessarily correspond to distinct textual revisions.

| Column        | Description                                                                |
|---------------|----------------------------------------------------------------------------|
| `edition_id`  | Unique publication-record identifier.                                      |
| `work_id`     | Reference to `works.work_id`.                                              |
| `title`       | Title of the associated work.                                              |
| `year`        | Publication year assigned to the record, including later reissues.         |
| `impression`  | Printing year, where separately recorded.                                  |
| `designation` | Edition or printing designation, retaining bibliographical qualifications. |
| `pages`       | Recorded pagination or extent.                                             |
| `status`      | Bibliographical verification status.                                       |
| `source`      | Catalogue, bibliographical or digital-witness reference URL.               |
| `note`        | Additional information concerning dating, editions, impressions or issues. |

A source may refer to a later edition whose publication history provides evidence of an earlier publication rather than to a copy of the publication itself.

## contributors.csv

Records of authors, editors, translators and other contributors associated with the series.

| Column           | Description                                                                     |
|------------------|---------------------------------------------------------------------------------|
| `contributor_id` | Unique contributor identifier.                                                  |
| `name`           | Recorded personal name.                                                         |
| `dates`          | Life dates, where available.                                                    |
| `roles`          | Roles and responsibilities associated with the series, separated by semicolons. |
| `umt_titles`     | Number of titled volumes linked to the contributor in the inventory.            |
| `work_ids`       | References to `works.work_id`, separated by semicolons.                         |
| `source`         | Biographical or bibliographical reference URL.                                  |

Contributor roles and work associations reflect the available evidence rather than a complete record of participation in the series. A zero in `umt_titles` indicates that no individual work has been linked to the contributor.

## translations.csv

Records of identified translations and bibliographical leads, including distinct issues and undated attestations.

| Column             | Description                                                              |
|--------------------|--------------------------------------------------------------------------|
| `translation_id`   | Unique translation-record identifier.                                    |
| `work_id`          | Reference to the original work in `works.work_id`.                       |
| `original_title`   | Title of the original work.                                              |
| `translated_title` | Recorded title of the translation.                                       |
| `language`         | Language of the translation.                                             |
| `date`             | Publication date or approximate dating, retaining source qualifications. |
| `translator`       | Translator or recorded statement of responsibility.                      |
| `publisher`        | Publisher of the translation.                                            |
| `status`           | Bibliographical verification status.                                     |
| `source`           | Catalogue, contemporary notice or other bibliographical reference URL.   |

The `date` field may contain approximate dates, date ranges or undated designations and should not be treated as a uniformly numerical field.

## collections.csv

Selected institutional collections holding volumes of the series.

| Column            | Description                                                                |
|-------------------|----------------------------------------------------------------------------|
| `group`           | Geographical grouping.                                                     |
| `institution`     | Institution or named collection.                                           |
| `country`         | Country in which the collection is located.                                |
| `titles`          | Number of inventory titles identified in the retrieved holdings records.   |
| `edition_records` | Number of publication or holdings groupings retrieved for the institution. |
| `access_note`     | Information concerning consultation or loan conditions.                    |
| `example_record`  | Illustrative catalogue-record URL.                                         |

Holdings counts reflect the available catalogue evidence rather than comprehensive collection surveys. Counts overlap between institutions and do not represent distinct titles or physical copies across collections.

## digital_access.csv

One summary of digital availability per titled volume.

| Column               | Description                                                                                   |
|----------------------|-----------------------------------------------------------------------------------------------|
| `work_id`            | Unique reference to `works.work_id`.                                                          |
| `title`              | Title of the associated work.                                                                 |
| `access`             | Digital-access and verification status.                                                       |
| `downloaded_objects` | Number of distinct digital objects retrieved, after consolidation of known duplicates.        |
| `inspected_editions` | Textual description of publications identified through inspection of their identifying pages. |
| `best_item`          | Selected external digital-library or item-record URL.                                         |
| `pdf`                | External PDF URL, where recorded.                                                             |
| `note`               | Additional information concerning access, identification or completeness.                     |

The `downloaded_objects` field counts digital objects rather than distinct editions. The `inspected_editions` field contains descriptive text rather than normalized edition references.

Digital-access information reflects the time of the survey and does not establish current availability or redistribution rights.

## Relationships between tables

The `work_id` field connects the principal bibliographical tables:

| Table                | Relationship to `works.csv`                                            |
|----------------------|------------------------------------------------------------------------|
| `editions.csv`       | Multiple publication records may reference the same work.              |
| `translations.csv`   | Multiple translation records may reference the same work.              |
| `contributors.csv`   | Contributors may be associated with multiple works through `work_ids`. |
| `digital_access.csv` | One digital-access summary per work.                                   |

Use work identifiers rather than titles when joining tables. Identifiers are local to this inventory and should not be interpreted as independent bibliographical evidence.

The collections table contains aggregate institutional information rather than individual work or copy associations.

## Verification and access categories

The following tables reproduce the status labels used in the CSV files.

### Publication records

| Status                             | Description                                                                                                      |
|------------------------------------|------------------------------------------------------------------------------------------------------------------|
| `Catalogue-supported; provisional` | Supported by catalogue records or publication-history evidence, without confirmed inspection of a matching copy. |
| `Identifying pages inspected`      | Title or publication-history pages of a digital witness have been examined.                                      |
| `Metadata lead only`               | Bibliographical lead requiring further verification.                                                             |

### Translation records

| Status                                | Description                                                                                          |
|---------------------------------------|------------------------------------------------------------------------------------------------------|
| `Catalogue-supported; copy unchecked` | Supported by catalogue evidence, without inspection of the translated copy.                          |
| `Translation attested; issue undated` | Translation attested by bibliographical evidence, with no established issue date.                    |
| `Contemporary notice; copy unchecked` | Supported by a contemporary notice, without verification of the copy or precise publication details. |
| `Lead; item verification needed`      | Tentative record requiring further bibliographical verification.                                     |

### Digital access

| Status                                  | Description                                                                                  |
|-----------------------------------------|----------------------------------------------------------------------------------------------|
| `Open PDF; identifying pages inspected` | Public PDF access recorded and identifying pages examined.                                   |
| `Open PDF; edition not verified`        | Public PDF access recorded, but publication identity has not been established.               |
| `Restricted scans / untested leads`     | Restricted digitizations or leads for which full page-image access has not been established. |
| `No digitized copy located`             | No digitized copy identified during the survey.                                              |

Inspection of identifying pages does not imply inspection of the entire volume or collation against other editions.

The works, contributors and collections tables do not have uniform record-level verification categories.

For further information on bibliographical verification, source provenance and limitations, see [DATA_QUALITY.md](DATA_QUALITY.md).
