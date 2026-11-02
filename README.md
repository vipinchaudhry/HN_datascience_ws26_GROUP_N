# Beyond Party Lines: Uncovering the Patterns Behind European Parliament Voting Behaviour

Data science elective project, TUM Campus Heilbronn, WS 2026/27.
Team: Anusha Reddy Mareddy, Kabir Ahmed, Vipin Chaudhry

Status: planning. Plan due Nov 4 2026, final submission due Jan 25 2027.

## Dataset

We use the HowTheyVote.eu roll-call voting data for the European Parliament.

- Source: https://github.com/HowTheyVote/data
- **Pinned release: `2026-11-01`**
  (https://github.com/HowTheyVote/data/releases/tag/2026-11-01)
- Snapshot timestamp (from the metadata files, `dc:created`): 2026-11-01T21:47:31 UTC
- Downloaded on: <date>, file `export.zip`
- Publisher: https://howtheyvote.eu

The dataset is published weekly and is marked experimental by its authors,
so table formats may change. **We analyse only the pinned release and do not
re-download newer ones**, so that all results are reproducible by every team member.

## License and attribution

The data is released under the Open Database License (ODbL 1.0).
Attribution to HowTheyVote.eu is required in all outputs. Terms:
https://howtheyvote.eu/about#license

Our code is released under the MIT License (see `LICENSE`). The MIT License
covers our code only, not the data.

## Repository layout

```
data/raw/        unzipped export, never edited (CSVs are not tracked in git)
data/processed/  cleaned tables produced by our code
notebooks/       analysis notebooks, numbered in order
src/             reusable code
story/           the visual data story
```

Rule: `data/raw/` is read-only. Every processed file must be reproducible from code.

## Getting the data

The raw CSVs are too large for GitHub (`member_votes.csv` is about 784 MB), so they
are not in the repository. Each team member downloads them once:

1. Go to the release page linked above.
2. Download `export.zip` from the assets at the bottom.
3. Unzip the CSV files into `data/raw/`.
4. Check that `data/raw/last_updated.txt` matches the file in the repository.

## Known limitations

- Only roll-call votes are included, not every vote held in Parliament.
  Our findings apply to recorded votes only.
- Several fields exist only for votes from 2024 onward (amendment details,
  result, majority type).
- The dataset format is experimental.
- `DID_NOT_VOTE` means absence, not disagreement. Our handling of it is documented
  in the notebooks.

## Research questions

**Main question:** To what extent is voting behaviour in the European Parliament
influenced by political group affiliation, national affiliation and the subject of
parliamentary decisions?

1. **Group loyalty:** How cohesively does each political group vote, and when do
   members defect from their group's majority position?
2. **National influence:** Do MEPs vote alike by country or national party beyond
   what their political group explains?
3. **Cross-party cooperation:** Which political groups exhibit unexpected voting
   similarities, and on which issues do these similarities occur?
4. **Policy differences:** How does voting alignment between political groups vary
   across policy areas?
5. **Change over time:** How have voting patterns and alignments evolved across the
   current and previous parliamentary term? (Conditional on consistent MEP IDs and
   group codes across terms; otherwise limited to a single term.)

### Working hypotheses (to be tested, not assumed)

- H1: Group explains most voting, but national party adds measurable explanatory power.
- H2: Group cohesion varies by topic.
- H3: Data-driven MEP clusters match official groups except for specific exceptions.

### Still to decide

- Treatment of `DID_NOT_VOTE`
- All votes vs. main votes only (`is_main`)
- Single term vs. two terms (after data checks)

## Setup

Python version, how to install requirements and how to run the notebooks: to be added.