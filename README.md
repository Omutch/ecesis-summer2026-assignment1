# Ecesis Investments Summer 2026 Assignment 1

## Assignment
Constraint Mapping Across Data Sources

## Overview
This project was completed for the Ecesis Investments 2026 Summer Power Systems Modeling Internship recruiting process.

The goal of the assignment was to map constraints across three different sources:

- PJMISO Market data
- Dayzer
- Panorama

Because each source uses different naming conventions and levels of detail, the project uses text normalization, fuzzy string matching, and confidence thresholds to identify likely corresponding constraints across the datasets.

## Files Included

### Notebook
- `notebooks/assignment1_constraint_mapping.ipynb`  
  Shows the full data loading, cleaning, matching, confidence scoring, and output generation process.

### Final Output
- `output/matched_constraints.csv`  
  Final required output file with the columns:
  - `market_constraint`
  - `dayzer_constraint`
  - `pano_constraint`

### Review Files
- `output/matched_constraints_with_scores.csv`  
  Includes match scores and confidence labels for review.

- `output/questionable_matches_for_review.csv`  
  Contains matches that may require additional manual review.

- `output/match_summary_statistics.csv`  
  Summarizes the match confidence levels.

### Report
- `report/assignment1_summary_report.pdf`  
  Summary report explaining the objective, methodology, results, insights, and conclusions.

## Method Summary
The matching process used the PJMISO Market dataset as the base dataset. Each Market constraint was compared against the Dayzer and Panorama constraint lists after cleaning and standardizing the text.

The cleaning process included:

- converting text to lowercase
- standardizing voltage formatting
- removing punctuation and extra separators
- replacing common abbreviations
- removing extra spaces

Matches were classified using confidence thresholds:

- 90 to 100: high confidence
- 80 to 89: medium confidence
- 70 to 79: low confidence
- below 70: weak confidence

For the final output, high and medium confidence matches were kept, while low and weak confidence matches were left blank to avoid forcing uncertain matches.

## Tools Used
- Python
- Jupyter Notebook
- pandas
- NumPy
- RapidFuzz
- matplotlib