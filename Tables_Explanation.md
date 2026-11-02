## Status
The dataset is experimental and the format of the tables may change in the future.

## License
The HowTheyVote.eu data is made available under an open license. If you use data published by HowTheyVote.eu please make sure you’ve read the [license terms](https://howtheyvote.eu/about#license) and provide proper attribution.

## Tables

### members.csv

Each row represents a Member of the European Parliament (MEP).

| Column          | Type              | Description                                                                            |
|-----------------|-------------------|----------------------------------------------------------------------------------------|
| `id`            | integer           | Member ID as used by the [MEP Directory](https://www.europarl.europa.eu/meps/en/home). |
| `first_name`    | string            | First name                                                                             |
| `last_name`     | string            | Last name                                                                              |
| `country_code`  | string            | 3-letter ISO-3166-1 code                                                               |
| `date_of_birth` | date (optional)   | Date of birth                                                                          |
| `email`         | string (optional) | Email address                                                                          |
| `facebook`      | string (optional) | Facebook profile URL                                                                   |
| `twitter`       | string (optional) | Twitter account URL                                                                    |

### countries.csv

Each row represents an EU member state.

| Column        | Type   | Description                                                         |
|---------------|--------|---------------------------------------------------------------------|
| `code`        | string | 3-letter ISO-3166-1 code                                            |
| `iso_alpha_2` | string | 2-letter ISO-3166-1 code                                            |
| `label`       | string | Label as published by the Publications Office of the European Union |

### groups.csv

Each row represents a political group in the European Parliament.

| Column           | Type   | Description                                                                                       |
|------------------|--------|---------------------------------------------------------------------------------------------------|
| `code`           | string | Unique identifier for the political group                                                         |
| `official_label` | string | Official label as published by the Publications Office of the European Union                      |
| `label`          | string | Label based on the official label. Prefixes and suffixes such as "Group" are removed for clarity. |
| `short_label`    | string | Short label or abbreviation                                                                       |

### group_memberships.csv

Each row represents a membership of an MEP in a political group.

MEPs can change their political group during the term, i.e., each MEP is part of one or
more political groups over the course of a term. Non-attached MEPs are a member of the
`NI` group.

| Column       | Type            | Description                                                 |
|--------------|-----------------|-------------------------------------------------------------|
| `member_id`  | integer         | Member ID                                                   |
| `group_code` | string          | Group code                                                  |
| `term`       | integer         | Parliamentary term                                          |
| `start_date` | date            | Start date                                                  |
| `end_date`   | date (optional) | End date. If empty, the MEP the membership is still active. |

### national_parties.csv

Each row represents a national party that an MEP belongs to.
For each parliamentary term, each national party is listed as a separate entity.
This is how the EP Open Data Portal lists the national parties, and we reuse this data.

| Column         | Type              | Description                                                                                  |
|----------------|-------------------|----------------------------------------------------------------------------------------------|
| `id`           | string            | ID of the national party as listed in the EP corporate bodies list                           |
| `label`        | string            | The official name of the party                                                               |
| `short_label`  | string            | The short label/abbreviation of the party                                                    |
| `start_date`   | string            | When the party was founded (if founded during a term), otherwise start of the relevant term. |
| `end_date`     | string (optional) | When the party ceased to exist or the relevant term ended. Empty if ongoing.                 |
| `country_code` | string            | Country code from the home country of the party.                                             |

### national_party_memberships.csv

Each row represents a membership of an MEP in a national party.

MEPs can change their national party during the term, i.e., each MEP is part of one or
more political groups over the course of a term.

| Column              | Type            | Description                                                                                    |
|---------------------|-----------------|------------------------------------------------------------------------------------------------|
| `member_id`         | integer         | Member ID                                                                                      |
| `national_party_id` | string          | National Party ID                                                                              |
| `start_date`        | date            | Start of the membership. Either when an MEP became a member of the party or start of the term. |
| `end_date`          | date (optional) | End of the membership if MEP left or term ended. Empty as long as membership is active.        |

### votes.csv

Each row represents a roll-call vote in plenary.

| Column                    | Type              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `id`                      | integer           | Vote ID                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `timestamp`               | dateTime          | Date and time of the vote                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `display_title`           | string (optional) | Title that can be used to refer to the vote. In most cases, this is the title published in the roll-call vote results. If the title in the roll-call vote results is empty, this falls back to the procedure title.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `reference`               | string (optional) | Reference to a plenary document such as a report or a resolution                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `description`             | string (optional) | Description of the vote as published in the roll-call vote results                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `amendment_subject`       | string (optional) | Subject of the specific amendment if applicable. This field is only available for votes starting in 2024                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `amendment_number`        | string (optional) | Number of the specific amendment if applicable. This field is only available for votes starting in 2024                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `is_main`                 | boolean           | Whether this vote is a main vote. We classify certain votes as main votes based on the text description in the voting records published by Parliament. For example, if Parliament has voted on amendments, only the vote on the text as a whole is classified as a main vote. Certain votes such as votes on the agenda are not classified as main votes. This is not an official classification by the European Parliament and there may be false negatives.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `procedure_reference`     | string (optional) | Procedure reference as listed in the Legislative Observatory                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `procedure_title`         | string (optional) | Title of the legislative procedure as listed in the Legislative Observatory                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `procedure_type`          | string (optional) | Procedure type as listed in the Legislative Observatory. This is a 3-letter code such as COD, RSP, or BUD.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `procedure_stage`         | string (optional) | Stage of the procedure in which the vote took place. One of `OLP_FIRST_READING`, `OLP_SECOND_READING`, `OLP_THIRD_READING`.This field is only available for votes starting in 2024 and if the vote is part of an Ordinary Legislative Procedure.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `majority_type`           | string (optional) | Type of majority required for this vote to pass. Only available for votes starting in 2024 and held as part of one of the following procedure types: * Ordinary Legislative Procedure (COD) * Own-Initiative Procedure (INI) * Resolutions on topical subjects (RSP) The majority is also available for votes on motions of censure against the Commission. We follow the naming used in the Rules of Procedure: * `MAJORITY_OF_VOTES_CAST`: Requires more votes for than against, ignoring abstentions and   MEPs that did not vote. * `MAJORITY_OF_COMPONENT_MEMBERS`: Requires more than half of votes cast, including   abstentions and MEPs that did not vote. For the 10th legislative term, this means 361   MEPs have to vote for. * `MAJORITY_OF_COMPONENT_MEMBERS`: Requires more than half of all MEPs in Parliament to   vote in favor, including abstentions and MEPs that did not vote. For the 10th legislative   term, this means 361 MEPs have to vote in favor. |
| `count_for`               | integer           | Number of MEPs who voted in favor                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `count_against`           | integer           | Number of MEPs who voted against                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `count_abstention`        | integer           | Number of MEPs who abstained                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `count_did_not_vote`      | integer           | Number of MEPs who didn’t participate in the vote                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `result`                  | string (optional) | Vote result. One of `ADOPTED`, `REJECTED`, `LAPSED`. This field is only available for votes starting in 2024.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `texts_adopted_reference` | string (optional) | "EP reference number of the text as it was adopted. This includes all amendments that were adopted to an original text.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### member_votes.csv

Each row represents how an MEP voted in a roll-call vote.

| Column                       | Type              | Description                                                                                                                                                                                                                                   |
|------------------------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `vote_id`                    | integer           | Vote ID                                                                                                                                                                                                                                       |
| `member_id`                  | integer           | Member ID                                                                                                                                                                                                                                     |
| `position`                   | string            | Vote position. One of `FOR`, `AGAINST`, `ABSTENTION` if the MEP participated in the vote or `DID_NOT_VOTE` if the MEP wasn’t present for the vote. We currently do not differentiate between MEPs who did not vote with or without an excuse. |
| `country_code`               | string            | Country code                                                                                                                                                                                                                                  |
| `group_code`                 | string (optional) | Group code. This references the political group that the MEP was part of on the day of the vote. This is not necessarily the MEP’s current political group.                                                                                   |
| `group_short_label`          | string (optional) | Short label of the political group that the MEP was part of on the day of the vote. This is not necessarily the MEP’s current political group.                                                                                                |
| `national_party_id`          | string (optional) | National party ID. This references the national party that the MEP was part of on the day of the vote. This is not necessarily the MEP’s current national party.                                                                              |
| `national_party_short_label` | string (optional) | Short label of the national party that the MEP was part of on the day of the vote. This is not necessarily the MEP's current national party.                                                                                                  |

### eurovoc_concepts.csv

Each row represents a concept from the [EuroVoc thesaurus](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/eurovoc)
that is referenced by at least one vote.

| Column   | Type   | Description        |
|----------|--------|--------------------|
| `id`     | string | EuroVoc concept ID |
| `label`  | string | Label              |

### eurovoc_concept_votes.csv

Each row represents an EuroVoc concept related to a vote.

| Column               | Type    | Description        |
|----------------------|---------|--------------------|
| `vote_id`            | integer | Vote ID            |
| `eurovoc_concept_id` | string  | EuroVoc concept ID |

### oeil_subjects.csv

Each row represents a subject as used by the [Legislative Observatory](https://oeil.europarl.europa.eu/oeil/en)
that is referenced by at least one vote.

| Column   | Type   | Description   |
|----------|--------|---------------|
| `code`   | string | Code          |
| `label`  | string | Label         |

### oeil_subject_votes.csv

Each row represents a subject related to a vote.

| Column              | Type    | Description   |
|---------------------|---------|---------------|
| `vote_id`           | integer | Vote ID       |
| `oeil_subject_code` | string  | Subject code  |

### geo_areas.csv

Each row represents a country, territory, or other geopolitical entity that is
referenced by at least one vote. The information is based on the [reference dataset](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/country)
published by the EU Publications Office.

| Column        | Type              | Description                                                            |
|---------------|-------------------|------------------------------------------------------------------------|
| `code`        | string            | ISO 3166-1 alpha-3 code if available, otherwise a custom 3-letter code |
| `label`       | string            | Label                                                                  |
| `iso_alpha_2` | string (optional) | ISO 3166-1 alpha-2 code if available                                   |

### geo_area_votes.csv

Country, territory, or other geopolitical entity related to a vote.

| Column          | Type    | Description          |
|-----------------|---------|----------------------|
| `vote_id`       | integer | Vote ID              |
| `geo_area_code` | string  | Geographic area code |

### committees.csv

Each row represents a committee of the European Parliament.

| Column         | Type   | Description                        |
|----------------|--------|------------------------------------|
| `code`         | string | Unique identifier of the committee |
| `label`        | string | Label                              |
| `abbreviation` | string | Abbreviation                       |

### responsible_committee_votes.csv

Committee responsible for the legislative procedure a vote is part of.

| Column           | Type    | Description    |
|------------------|---------|----------------|
| `vote_id`        | integer | Vote ID        |
| `committee_code` | string  | Committee code |

### amendment_authors_votes.csv

Authors of the vote if vote is amendment. Multiple authors result in multiple rows.
This information is only available for votes starting in 2024.

| Column           | Type    | Description                                                                        |
|------------------|---------|------------------------------------------------------------------------------------|
| `vote_id`        | integer | Vote ID                                                                            |
| `author_type`    | string  | Either `GROUP`, `COMMITTEE`, `MEMBERS`, `ORALLY`, `ORIGINAL_TEXT`, or `RAPPORTEUR` |
| `group_code`     | string  | Group code, if applicable.                                                         |
| `committee_code` | string  | Committee code, if applicable.                                                     |

### amendment_urls.csv

URLs of amendments linked to a vote.

| Column             | Type    | Description                                                                                                                                                                                                              |
|--------------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `vote_id`          | integer | Vote ID                                                                                                                                                                                                                  |
| `amendment_number` | integer | Amendment number.                                                                                                                                                                                                        |
| `url`              | string  | Links to PDF documents containing the text of the amendments. The linked documents may contain multiple amendments, not just the amendments the vote was about. This field is only available for votes starting in 2024. |

### groups_required_for_majority.csv

Each row represents a combination of political groups required for a majority in a
vote. That is, the vote would not have passed if the MEPs of the groups that voted in
favor would have voted against.

We calculate this information based on the majority type of a vote. It is currently only
available for votes starting in 2024 and held as part of one of the following procedure
types:

* Ordinary Legislative Procedure (COD)
* Own-initiative Procedure (INI)
* Resolutions on topical subjects (RSP)

The required groups are also available for votes on motions of censure against the
Commission.

We list only the minimal combinations of group that are required for a majority. For
example, if the ECR are required for the majority to hold, that implies that any
combination of the ECR with another group is also required, but we only list ECR.

| Column        | Type    | Description                                     |
|---------------|---------|-------------------------------------------------|
| `vote_id`     | integer | Vote ID                                         |
| `group_codes` | string  | Political group codes, concatenated with a `+`. |
