This MATLAB script is designed to analyze time-resolved fluorescence data, specifically focusing on vesicle release and FRET (Förster Resonance Energy Transfer) signals. It aims to synchronize and analyze these signals around the vesicle release event (defined as the "drop").

Purpose:

The script processes .mat files containing time-series data related to vesicle intensity and FRET ratios, aligns them to a common time point (the vesicle drop), calculates mean and SEM (standard error of the mean), generates plots, and saves the results to CSV files.

How to Use:

Data Preparation:

Ensure you have .mat files in the same directory as the MATLAB script.
Each .mat file should contain a structure named selection with the following fields:
selection.vesicleValues: Time-series data of vesicle intensity.
selection.ratioValues: Time-series data of FRET ratio.
selection.timePoints: Time points corresponding to the data.
MATLAB Setup:

Open MATLAB.
Set the current working directory to the folder containing your .mat files and the script.
Copy and paste the code into a new MATLAB script file (.m file).
Run the Script:

Run the script. MATLAB will:
Load data from all vesicle*.mat files.
Perform the analysis steps described below.
Generate plots.
Save the results to CSV files.
What the Script Achieves:

Data Loading and Preprocessing:

Loads data from .mat files.
Smooths the vesicle intensity data using a moving average.
Detects the vesicle drop onset (time zero) by finding the minimum derivative of the smoothed vesicle intensity.
Defines a time window around the drop onset.
Aligns the vesicle and FRET signals to the drop onset (t=0).
Normalizes the vesicle and FRET signals to a baseline value (median of pre-drop data).
Detects the FRET drop onset (time of the most negative slope in the FRET ratio before vesicle drop).
Data Synchronization and Averaging:

Pads the aligned traces with NaN values to ensure they have the same length.
Calculates the mean and SEM for the vesicle and FRET signals across all traces.
Visualization:

Generates a plot of the mean vesicle and FRET signals ± SEM, aligned to the vesicle drop.
Generates a histogram of the FRET drop onset times relative to the vesicle drop.
Statistical Analysis:

Calculates the mean FRET drop onset time.
Calculates the percentage of FRET drops that occurred before vesicle release.
Data Export:

Saves the mean and SEM data to a CSV file (Aligned_Mean_SEM_DropOnset.csv).
Saves all synchronized individual traces to a CSV file (All_Synchronized_Traces.csv).
Key Analysis Steps Explained:

Vesicle Drop Detection:
The script finds the time point where the vesicle signal rapidly decreases, indicating vesicle release.
This is done by finding the minimum of the derivative of the smoothed vesicle signal.
FRET Drop Detection:
The script finds the time point where the FRET ratio rapidly decreases before the vesicle drop.
This is done by finding the minimum of the derivative of the smoothed FRET ratio in the pre-drop time window.
Normalization:
The vesicle and FRET signals are normalized to a baseline value, typically the median value in a pre-drop time window.
This allows for comparison of signals across different experiments.
Synchronization:
All traces are aligned to the vesicle drop onset (t=0).
This allows for averaging and comparison of signals across different experiments.
Mean and SEM Calculation:
The mean and SEM are calculated for the vesicle and FRET signals at each time point.
This provides a measure of the average signal and its variability.
What You Achieve:

Synchronization of Time-Series Data: Aligns vesicle and FRET signals to the vesicle release event.
Averaged Signal Analysis: Provides mean and SEM plots, representing the average behavior of the vesicle and FRET signals.
FRET Drop Timing Analysis: Quantifies the timing of the FRET drop relative to vesicle release.
Data Export for Further Analysis: Saves the processed data to CSV files for use in other software.
This script is useful for analyzing time-resolved fluorescence data related to vesicle release and FRET, providing insights into the timing and dynamics of these events.
