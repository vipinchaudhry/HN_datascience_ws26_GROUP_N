# Beyond Party Lines: Uncovering the Patterns Behind European Parliament Voting Behaviour

Data science elective project, TUM Campus Heilbronn, WS 2026/27.
Team: Anusha Reddy Mareddy, Kabir Ahmed, Vipin Chaudhry

Status: planning. Plan due Nov 4 2026, final submission due Jan 5 2027

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

## Repository layout

```
data/raw/        unzipped export, never edited
data/processed/  cleaned tables produced by our code
notebooks/       analysis notebooks, numbered in order
src/             reusable code
story/           the visual data story
```

Rule: `data/raw/` is read-only. Every processed file must be reproducible from code.

## Known limitations

- Only roll-call votes are included, not every vote held in Parliament.
  Our findings apply to recorded votes only.
- Several fields exist only for votes from 2024 onward (amendment details,
  result, majority type).
- The dataset format is experimental.

## Research questions (draft)
### WE NEED TO DECIDE ON THESE;
### NOT YET FIXED

Main research question
To what extent is voting behaviour in the European Parliament influenced by political group affiliation, national affiliation and the subject of parliamentary decisions?
Sub-research questions
1. Political group loyalty: How consistently do Members of the European Parliament (MEPs) vote in accordance with the majority position of their political group?

2. National influence: Do MEPs from the same country demonstrate similar voting behaviour, even when they belong to different political groups?

3. Cross-party cooperation: Which political groups exhibit unexpected voting similarities, and on which issues do these similarities occur?

4. Policy differences: How does voting alignment between political groups vary across different policy areas?

5. Changes over time: How have voting patterns and political alignments evolved throughout the current and previous parliamentary terms?

## Setup

### Python version, how to install requirements, how to run the notebooks
### will do later as well