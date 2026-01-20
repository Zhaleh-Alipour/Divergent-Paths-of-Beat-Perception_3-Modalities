# explanatory_analysis

## item_analysis

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

- **Note**
  This item analysis was performed on preliminary data from 19 participants.
  The resulting trial selection was then used in the final experiment documented in this repository.

⚠️ Important:
  The code in this folder is provided for demonstration and reproducibility purposes only.
  The trial removal has already been applied in the current version of the experiment.

  As a result:
  The experiment and the item analysis result contains 21 trials instead of the original 30.
  The item analysis code will reproduce the analysis process, not modify the experiment further. 

---

## vis_speed_filter

- **Description**
  In this experiment, each trial was presented at one of three tempi: 230 ms, 250 ms, or 270 ms.
  This code analyzes participants’ performance on visual trials at a single specified tempo, allowing tempo-specific evaluation of visual performance.

- **Purpose**
  This analysis was motivated by a reviewer comment during the peer-review process. The reviewer raised concerns about monitor refresh rates potentially affecting the temporal fidelity of visual stimulus presentation.

  Standard monitor refresh rates (e.g., 30 Hz, 60 Hz, 120 Hz) impose constraints on stimulus timing. Some inter-stimulus intervals align cleanly with these refresh rates, while others do not:

  230 ms: does not align with standard refresh rates
  250 ms: aligns with 60 Hz and 120 Hz (but not 30 Hz)
  270 ms: does not align with standard refresh rates

  When stimulus timing does not align with the monitor’s refresh cycle, the actual presentation intervals may vary slightly across trials. This inconsistency is especially problematic for visual beat sequences, where precise temporal regularity is critical for preserving the beat structure. Such timing distortions may partially explain why performance on visual beat sequences was lower than on non-beat sequences.

  All participants completed the experiment on lab monitors operating at 60 Hz. Therefore, if refresh-rate alignment influenced performance, we would expect better visual performance at the 250 ms tempo compared to 230 ms and 270 ms especially on beat sequence blocks.

  This code tests that hypothesis by isolating and analyzing visual block performance as a function of tempo.

- **Input:**  
  `data/2_preprocessed_data` and then `json_vis230_Only` or `json_vis250_Only` or `json_vis270_Only`

- **Analysis code:**  
  `visual_speed_filter.js`

- **Outputs:** 
  `results/Visual_230_Only.xlsx` or `results/Visual_250_Only.xlsx` or `results/Visual_270_Only.xlsx`

- **Note**
  To run the analysis for a specific tempo:
  Set the speedFilter constant in visual_speed_filter.js to the desired tempo value (1=230, 2=250, or 3=270).
  Update the input file `json_vis230_Only` and output file `results/Visual_230_Only.xlsx` to match the selected tempo. 

--- 

## visualization of survey results.ipynb
  This script performs exploratory data analysis (EDA) on end-of-study questionnaire data collected as part of the study. The analysis pipeline begins with data preprocessing and concludes with visualizations that summarize key characteristics of participants’ musical training.