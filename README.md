# Divergent Paths of Beat Perception_3 Modalities

This repository contains the code, data (sample and derived), and analysis pipelines used in the PhD project **Divergent Paths of Beat Perception_3 Modalities**.  
The project investigates how lower-level timing abilities contribute to beat perception across auditory, visual, and tactile modalities.

## Repository structure

- `Experiment/`  
  PsychoPy experiment code and stimuli used to collect behavioral data from participants.  
  See `Experiment/README.md` for full experimental details and instructions.

- `data/`  
  Raw (not shared), sample, and derived datasets, along with documentation describing data availability and generation.  
  See `data/README.md` for details.

- `raw_to_preprocessed/`  
  Scripts used to preprocess raw data files into preprocessed files.
  See `raw_to_preprocessed/README.md` for details.

- `preprocessed_to_xlsx/`  
  Scripts for converting preprocessed data into structured formats used in downstream analyses.
  See `preprocessed_to_xlsx/README.md` for details.

- `end_of_study_questionnaire`
  Script for deriving information of interest from the questionnair responses.

- `exploratory_analysis/`  
  Scripts for exploratory data analysis (EDA), including trial-level participant performance, visual-block performance as a function of stimulus presentation tempo, and visualization of survey results. 

- `results/`
  xlsx files containing questionnaire results as well as group-level and clustering results.
  See `results/README.md` for details.

- `clustering_analysis/`  
  Clustering analyses (Silhouette analysis and K-means) used to group participants based on their performance.
  See `clustering_analysis/README.md` for details.

- `visualization/`  
  Code for generating figures and visualizations.

- `plots/`  
  Generated plots and figures used in analyses and manuscripts.

## Data availability

Full raw experimental and questionnaire data are not publicly shared due to participant privacy considerations.  
Sample data and all preprocessing and analysis code are provided to support reproducibility.


## License

This project is released under the MIT License.

## Contact

**Zhaleh Mohammad Alipour**  
📧 zhaleh.m.alipour@gmail.com