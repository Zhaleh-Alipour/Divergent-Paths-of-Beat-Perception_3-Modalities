# Results

This folder contains outputs from different analyses or questionnaires performed in the project.

## end_of_study_Q.xlsx

- **Description:**  
  After the end of the experiment, participants completed a questionnaire created on Qualtrics that included biographical, music-related, and experiment-related questions.

- **Input:**  
  The original Excel file `data/End_of_study_questionnaire_141.xlsx` containing all participants’ raw questionnaire responses.
**Note:** This file is not shared but a sample of questionnaire file `End_of_study_Q_sample.xlsx` is shared for reproducing the code. 

- **Analysis:**  
  A preprocessing step was applied to the raw questionnaire data to extract variables of interest. This analysis is saved in `end_of_study_questionnaire/Qualtrics analysis.py`. The processed information was then compiled and saved into a cleaned output file.

- **Output:**  
  `end_of_study_Q.xlsx` — this file contains the variables required for inclusion in the final `report/`paper.

- **Notes:**  
  - Columns with labels such as `(>=5 -> 2)` indicate categorical encoding, where:
    - values **less than 5 years** are encoded as `1`
    - values **5 years or more** are encoded as `2`
  - The `unique_id` column represents the unique identifier assigned to each participant.

---

## predicted_results.xlsx

- **Description:**  
  This file contains synthetic data generated to visualize the four predicted patterns of performance expected after running the experiment.

- **Purpose:**  
  The synthetic dataset is used solely for visualization and illustration of expected outcome patterns, not for statistical analysis of real participant data.

- **Visualization code:**  
  `visualization/predicted_results.ipynb`

- **Output plot:**  
  `plots/predicted_results.png`

---

## PrimaryResults_141participants.xlsx

- **Description:**  
  This file contains the main results from all participants included in the study (**N = 141**).

- **Columns 2–7: Block-wise performance with detailed annotations**  
  These columns report participant performance across the nine experimental blocks.

  Block labels:
  - **SD** = Single Duration  
  - **Irreg** = Irregular (non-beat)  
  - **Reg** = Regular (beat)

  Data are presented in the following format: 0.79 [0] (0) {2}
where:
- `0.79` → mean performance for that block (per participant)
- `[ ]` → number of **attention-check failures**
- `( )` → number of **false alarms**, i.e., trials in which:
  - the trial was a normal trial (keys 1, 2, or 3 expected), but  
  - the participant responded with the attention-check key (`G`)
- `{ }` → number of **easy-trial failures** (present only in Single Duration blocks)

*Easy trials* are defined as trials in which the difference between standard and deviant durations is large (e.g., 1.4 vs. 4).  
These annotated values were used during preprocessing to identify and exclude low-quality participants from further analyses.

- **Columns 9–14: Mean block performance (cleaned)**  
These columns contain only the mean performance values for each block and participant, without additional annotations.

- **Columns 15–26: Transposed-interval difference metrics**  
These columns report the mean difference between transposed intervals for **correctly** and **incorrectly** answered trials in each block.

In each sequence trial of the experiment:
- Three stimuli were presented
- One stimulus was deviant, created by **transposing two intervals** in the sequence

Example:
- Standard stimulus: `22314`
- Deviant stimulus: `22134`  
  (intervals `1` and `3` are transposed)

In Single Duration trials, these values instead reflect the difference between standard and deviant durations.

These measures were derived to test the hypothesis that performance in beat (Reg) and non-beat (Irreg) blocks varies as a function of the magnitude of interval transposition—specifically, that larger differences facilitate discrimination.

For example:
- `AudRegIntDiff (T)` represents the average transposed-interval difference for **correct trials** in the auditory beat (regular) block.

- **Columns 28–33: Block presentation order**  
These columns indicate the order in which each block was presented to each participant.  
Block order was randomized across participants.

These data were later used to assess potential order effects, such as whether completing auditory blocks earlier improved performance in subsequent visual or tactile blocks.

---

## PreprocessedResults_MusicAdded.csv

- **Description:**  
  This spreadsheet is the preprocessed version of `PrimaryResults_141participants.xlsx`.

- **Participant exclusion criteria:**  
  After compiling results from all 141 participants, individuals were excluded from subsequent analyses if they met **any** of the following criteria:
  - Performance at chance level (33%) in **four or more blocks**
  - More than five Failure to correctly identify attention-check trials or false alarms.

  No participant was excluded in this study, yielding a final sample size of **N = 141**.

- **Additional variables:**  
  A column representing **years of musical instruction** was added from `end_of_study_Q.xlsx` to this dataset:
  - `1` → less than 5 years of musical instruction  
  - `2` → 5 or more years of musical instruction  

  This variable was required for subsequent statistical analyses and visualizations.

- **Column removal:**  
  Columns 2–7 from `PrimaryResults_141participants.xlsx` (block-wise performance with detailed annotations) were removed in this file, as they were not required for downstream analyses.

---

## Three_Auditory_clusters.csv  
## Three_Auditory_clusters_2.csv

- **Description:**  
  These files contain the results of a clustering analysis performed on the auditory modality data.

- **Analysis rationale:**  
  A Silhouette analysis indicated that **three clusters** provided the optimal clustering solution for auditory performance. Based on this result, participants were assigned to three clusters using a k-means clustering approach.

- **Input:**  
  `PreprocessedResults_MusicAdded.csv`

- **Analysis code:**  
  `clustering analysis/K-means/Inperson_auditory_kmeans.ipynb`

- **Outputs:**  
  - `Three_Auditory_clusters.csv`  
  - `Three_Auditory_clusters_2.csv`

- **Purpose:**  
  These datasets were generated for visualization purposes:
  - `Three_Auditory_clusters.csv` is used for **scatter plot** visualizations  
  - `Three_Auditory_clusters_2.csv` is used for **bar plot** visualizations  

  The final plots produced from these files are stored in the `plots/` folder.

- **Notes:**  
  - Column labels indicate cluster membership:
    - `0` → Cluster 1  
    - `1` → Cluster 2  
    - `2` → Cluster 3

---

## Two_Visual_clusters.csv  
## Two_Visual_clusters_2.csv

- **Description:**  
  These files contain the results of a clustering analysis performed on the visual modality data.

- **Analysis rationale:**  
  A Silhouette analysis indicated that **two clusters** provided the optimal clustering solution for visual performance. Based on this result, participants were assigned to two clusters using a k-means clustering approach.

- **Input:**  
  `PreprocessedResults_MusicAdded.csv`

- **Analysis code:**  
  `clustering analysis/K-means/Inperson_visual_kmeans.ipynb`

- **Outputs:**  
  - `Two_Visual_clusters.csv`  
  - `Two_Visual_clusters_2.csv`

- **Purpose:**  
  These datasets were generated for visualization purposes:
  - `Two_Visual_clusters.csv` is used for **scatter plot** visualizations  
  - `Two_Visual_clusters_2.csv` is used for **bar plot** visualizations  

  The final plots produced from these files are stored in the `plots/` folder.

- **Notes:**  
  - Column labels indicate cluster membership:
    - `0` → Cluster 1  
    - `1` → Cluster 2  

---

## Three_Tactile_clusters.csv  
## Three_Tactile_clusters_2.csv

- **Description:**  
  These files contain the results of a clustering analysis performed on the tactile modality data.

- **Analysis rationale:**  
  A Silhouette analysis indicated that **three clusters** provided the optimal clustering solution for tactile performance. Based on this result, participants were assigned to three clusters using a k-means clustering approach.

- **Input:**  
  `PreprocessedResults_MusicAdded.csv`

- **Analysis code:**  
  `clustering analysis/K-means/Inperson_tactile_kmeans.ipynb`

- **Outputs:**  
  - `Three_Tactile_clusters.csv`  
  - `Three_Tactile_clusters_2.csv`

- **Purpose:**  
  These datasets were generated for visualization purposes:
  - `Three_Tactile_clusters.csv` is used for **scatter plot** visualizations  
  - `Three_Tactile_clusters_2.csv` is used for **bar plot** visualizations  

  The final plots produced from these files are stored in the `plots/` folder.

- **Notes:**  
  - Column labels indicate cluster membership:
    - `0` → Cluster 1  
    - `1` → Cluster 2  
    - `2` → Cluster 3

---

## Item_Analysis.xlsx

- **Description**
  This file is the result of running item analysis that shows performance for each trial and each participant separately where 0 means they answered incorrectly to the trial and 1 means they answered correctly. 

- **Subsequent analysis on the result:**  
  After executing this analysis and getting the result, 1- in a specific modality and condition (e.g., auditory beat sequence block), we performed the correlation of each trial performance to overal performance (point-biserial correlation), 2- did the same analysis for the three modalities separately while the order of sequences were matched, 3- removed 9 trials (3 trials based on each modalities result) whose correlation was the lowest (i.e. the trials that are too difficult for participants and did not contribute to the overall performance) 

- **Input:**  
  `data/3_json_files`

- **Analysis code:**  
  `item_analysis/ItemAnalysis_inPerson.js`

- **Outputs:**  
  - `results/Item_Analysis.xlsx`  

- **Purpose:**  
  The purpose of running this analysis and the subsequent analysis was to remove some trials and decrease the size or length of blocks. This was done after most participants reported that the blocks and the whole experiment is too long and tiring for them to keep being focused. 

## Visual_230_Only.xlsx
## Visual_250_Only.xlsx
## Visual_270_Only.xlsx

- **Description**
  In this experiment, each trial was presented at one of three tempi: 230 ms, 250 ms, or 270 ms.
  These files show participants’ performance on visual trials at a single specified tempo, allowing tempo-specific evaluation of visual performance.
  The whole idea is that on a monitor with 60 Hz refresh rate, the duration of visual stimuli would align for 250 ms tempo but not for 230 or 270 ms. 

- **Subsequent analysis on the result:** 
We compare the results of visual blocks (especially beat sequence block) across the three tempi to see if performance is more accurate for 250 ms compared to 230 and 270 ms. 

- **Input:**  
  `data/2_preprocessed_data` and then `json_vis230_Only` or `json_vis250_Only` or `json_vis270_Only`

- **Analysis code:**  
  `visual_speed_filter.js`

- **Outputs:** 
  `results/Visual_230_Only.xlsx` or `results/Visual_250_Only.xlsx` or `results/Visual_270_Only.xlsx`