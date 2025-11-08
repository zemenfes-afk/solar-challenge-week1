# Interim Report: Solar Data Discovery

Name: zemenfes hailemariam 
Date: November 9, 2025

### Task 1 Summary (Git & Environment Setup)

The project environment has been successfully established.
* A GitHub repository (`solar-chall![img.png](img.png)enge-week1`) was created and cloned.
* A Python virtual environment (`venv`) was set up.
* A `.gitignore` file was configured to ignore data and environment files.
* A `requirements.txt` file was generated with all necessary libraries (pandas, streamlit, etc.).
* A GitHub Actions CI workflow (`ci.yml`) was implemented and successfully tested to ensure all dependencies install correctly.

### Task 2 Approach (Profiling, Cleaning & EDA Outline)

My approach for analyzing the data for Benin, Sierra Leone, and Togo is as follows:

1.  Isolate Work: Each country will be analyzed on a separate Git branch (`eda-benin`, `eda-sierraleone`, `eda-togo`) to keep work organized.
2.  Load Data: Load the raw CSV data for all locations within each country, combining them into a single DataFrame.
3.  Clean Data:
    * Handle file-specific issues like encoding errors (`latin1`) and extra header rows (units).
    * Convert all data to the correct types (e.g., `pd.to_datetime`, `pd.to_numeric`).
    * Profile missing values and drop or impute them (e.g., drop rows with missing GHI, impute `Tamb` with median).
    * Compute Z-scores for key metrics (GHI, DNI, DHI, WS) and filter outliers where `|Z-score| > 3`.
4.  Export: The cleaned DataFrame for each country will be exported to a `_clean.csv` file (e.g., `benin_clean.csv`).
5.  Visualize: Perform the required EDA by creating all plots:
    * Time Series plot (GHI vs. Timestamp)
    * Correlation Heatmap
    * RH vs. Tamb Scatter Plot
    * GHI Histogram
    * Bubble Chart (GHI vs. Tamb, size=RH)