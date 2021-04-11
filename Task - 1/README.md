
﻿

# **MIDAS Task 1**

```
Name - Prabhav Singh
Email Id - prabhavs.ic18@nsut.ac.in
```

## Introduction

Please go through the file - **[MIDAS_TASK1_Method.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/MIDAS_TASK1_Method.pdf"MIDAS_TASK1_Method.pdf") for a detailed explanation of all experiments performed.**
All models, training settings, results and references etc are defined there.

## Directory Structure

All files present are shown below. Please keep the directory structure the same. A few other points to note are:
1. The code was developed on Kaggle for ease of access to the data. Links for the same are:
```
Notebook 1 and 2 - https://www.kaggle.com/prabhavsingh/midas-task1-final
Notebook 3 - https://www.kaggle.com/prabhavsingh/fork-of-midas-task1-final
```
2. The folder Results/ contains all the CSV results submitted to Kaggle.
3. static/ contains images used in ReadMe

```
MIDAS_Submission_Prabhav/Task - 1
└── MIDAS_TASK1_Method.pdf
└── static/
└── Results/
	└── Submission1_Exp1_LogSpec.csv
	└── Submission2_Exp2_MFCCS.csv
	└── Submission3_Exp3_Deltas.csv
└── MIDAS_Task1_Exp1_LogSpec.ipynb
└── MIDAS_Task1_Exp2_MFCCs.ipynb
└── MIDAS_Task1_Exp3_Deltas.ipynb
```

## How to run

####  On Kaggle

1. Go to the links provided in the previous section.
2. Fork and Copy the Notebooks.
3. Run the Notebook on Kaggle with No GPU (For higher RAM).

#### Locally

 - First install the Git Repository.
 - Add data folders from Kaggle to the folder in the same format.
 - In a command prompt (Anaconda Preferred)
 ``` cmd
cd MIDAS_Submission_Prabhav
conda create --name <env> --file requirements.txt
cd Task - 1
```
- Run all notebooks normally.

## Flowcharts for Methodology

Please go through the file - **[MIDAS_TASK1_Method.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/MIDAS_TASK1_Method.pdf"MIDAS_TASL1_Method.pdf") for a detailed explanation of all experiments performed.**

Three methods were adopted seperately. The are:
1. Using Log Scaled Normalized Spetrograms
2. Using First 13 MFCCs
3. Using First 13 MFCCs and Higher Order Deltas.

The flowcharts are shown below:

| ![flow.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/static/flow.png) | 
|:--:| 
| *Method 1 - Spectrogram* |

The other two methods use the same procedure as shown above but have different feature extraction shown below:

| ![flow1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/static/flow1.png) | 
|:--:| 
| *Method 2 - MFCCs* |

| ![flow2.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/static/flow2.png) | 
|:--:| 
| *Method 3 - MFCCs and Deltas* |


## Results and Solutions

Detailed results are in  [MIDAS_TASK1_Method.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/MIDAS_TASK1_Method.pdf"MIDAS_TASL1_Method.pdf").

A screenshot of the same is given below:

| ![results.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%201/static/results.png) | 
|:--:| 
| *Screenshot of Results* |


## References

#### Reference In Text

[1] David S., Speech representation and Data Exploration
[2] Zero Padding and its Advantages
[3] Splitting Samples into Smaller Segments, Qing Wei
[4] Understanding the Mel Spectrogram, Leland Roberts
[5] Understanding MFCCs, Prateestha Nair
[6] MFCCs and its Features, Springer (Appendix) 
[7] Speaker Recognition Using MFCC and Delta Delta MFCCs with ANNs, Singh et al., IJARSE 2016
[8] Significance of prosodic features for automatic emotion recognition, John et al., AIP 2020

#### Reference Used for Development of Code

[1] Music Feature Extraction in Python, Saket Doshi
[2] Musical Instrument Sound Classification using CNN, Muhammad Ardi

