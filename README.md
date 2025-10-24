# Patient-Phenotyping-and-Clustering-Using-PySpark


## Overview
This project implements both **rule-based** and **unsupervised phenotyping** methods to identify **Type 2 Diabetes Mellitus (T2DM)** cases from large-scale electronic health-record (EHR) data.  
Using **PySpark (RDD API + MLlib)**, the workflow builds distributed pipelines for data integration, feature extraction, and clustering to uncover latent patient phenotypes.

## Data
The dataset consists of three de-identified tables:

- `diagnoses.csv` – ICD-9/10 diagnosis codes  
- `medications.csv` – prescribed drug codes  
- `lab_events.csv` – laboratory test results  

Each record is keyed by **patient ID**, enabling patient-level feature aggregation across multiple clinical sources.

## Methods

### 1. Rule-Based Phenotyping (Supervised)
- Implemented a simplified **PheKB-style algorithm** in PySpark.  
- Classified patients as *Case*, *Control*, or *Unknown* using thresholds on diagnosis counts, medication frequency, and lab values.  
- Generated gold-standard labels for later evaluation.

### 2. Feature Construction
- Aggregated raw EHR data into patient-level features:  
  - Counts of unique diagnoses and medications  
  - Average and max lab results  
- Normalized and assembled sparse feature vectors for clustering.

### 3. Unsupervised Learning
- Applied **K-Means** and **Gaussian Mixture Models (GMM)** using **Spark MLlib**.  
- Explored multiple K values and random initializations to test cluster stability.

### 4. Evaluation
- Compared clustering results with the rule-based labels using **cluster purity** and **normalized mutual information (NMI)**.  
- Visualized cluster distributions and phenotype separation.


## Results
- Successfully built a distributed ETL pipeline that processed thousands of patient records in parallel.  
- Rule-based algorithm accurately separated *case* and *control* populations.  
- **K-Means** produced interpretable clusters consistent with T2DM phenotypes; **GMM** captured subtler overlaps between groups.  
- Demonstrated scalable, interpretable patient phenotyping using Spark on healthcare big data.

## Tech Stack
- **Languages:** Python  
- **Libraries:** PySpark (RDD & MLlib), NumPy, SciPy, scikit-learn  
- **Platform:** Google Colab / Dataproc  
- **Data Format:** CSV → RDD → Feature Vectors  

## How to Run
1. Upload project folder to **Google Drive** or cluster environment.  
2. Open `BD4H_HW3.ipynb` in **Google Colab**.  
3. Mount Drive and update data paths in the first cell.  
4. Run all cells to generate labels, features, and clustering outputs.  
5. View evaluation metrics and cluster visualizations at the end of the notebook.

   
---

## Author
**Buddhika Patalee**  
Ph.D. Agricultural Economics | Data Scientist  
[Website](https://www.buddhikapatalee.com) • [LinkedIn](https://www.linkedin.com/in/buddhika-patalee-phd/)



