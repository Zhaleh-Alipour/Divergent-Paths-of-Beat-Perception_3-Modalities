# item_analysis

- **Description**
  This code performs an item analysis to compute performance for each trial and each participant separately.
  For each trial:
 - 0 indicates an incorrect response
 - 1 indicates a correct response
  The results are exported in a spreadsheet format for further statistical analysis.

- **Input:**  
  `data/3_json_files`

- **Analysis code:**  
  `item_analysis/ItemAnalysis_inPerson.js`

- **Outputs:**  
  - `results/Item_Analysis.xlsx`  
  An Excel file containing trial-level performance (0/1) for each participant, along with overall performance measures per modality and condition.

- **Subsequent analysis on the result:**  
  After generating Item_Analysis.xlsx, the following analyses were conducted:

 1- Within-modality analysis
    For each modality and condition (e.g., auditory beat sequence blocks), the performance of each trial was correlated with overall block performance using point-biserial correlation.

 2- Cross-modality comparison
    The same correlation analysis was performed separately for the three modalities, with trial order matched across modalities.

 3- Trial removal
    Based on these analyses, 9 trials were removed in total:
    - 3 trials per modality
    - Specifically, trials with the lowest correlations, indicating excessive difficulty and minimal contribution to overall performance.

- **Purpose:**  
  The goal of this analysis—and the subsequent trial removal—was to shorten the experimental blocks.
Many participants reported that the experiment was too long and fatiguing, making it difficult to maintain attention throughout.

Reducing the number of trials improved participant engagement while preserving meaningful performance measures.

  **Note**
  This item analysis was performed on preliminary data from 19 participants.
  The resulting trial selection was then used in the final experiment documented in this repository.

⚠️ Important:
  The code in this folder is provided for demonstration and reproducibility purposes only.
  The trial removal has already been applied in the current version of the experiment.

  As a result:
  The experiment and the item analysis result contains 21 trials instead of the original 30.
  The item analysis code will reproduce the analysis process, not modify the experiment further. 