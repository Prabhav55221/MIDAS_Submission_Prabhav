
# MIDAS - Task 3

_Prabhav Singh_
_Netaji Subhas Institute of Technology_
_Internship Task (MIDAS)_

Please refer to this [PDF document](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/MIDAS_Task3_Method.pdf) for the detailed methodology if the images don't load here.


## Index

1. Introduction
2. How To Run
3. Data Preview
4. Data Preprocessing Steps and Data Cleaning
5. Vectorization and Training
6. Results and Discussion 
7. Possible Improvements



## Introduction

**Task Statement:** Use a given dataset to build a model to predict the category using description. Write code in python. Using Jupyter notebook is encouraged.

| ![flow.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/flow.png) | 
|:--:| 
| *High Level Overview of Methodology* |

**Solution Statement:** A _TF-IDF based GRID-CV hypertuned SVC (Support Vector Classifier)_ was used on the dataset to predict the cleaned product category in two different ways, achieving an accuracy of **96% and 98%** respectively.

**Feature Selection:** A concatenation of Product Name and Product Description.

**Directory Structure:**
```
MIDAS_Submission_Prabhav
└── Task 3
	└── images
		└── (Images Used for ReadMe)
    └── MIDAS_Task3.ipynb
    └── flipkart_com-ecommerce_sample.csv
    └── Task3_ReadMe.md
```


## How To Run

#### Using Anaconda (Recommended)
``` cmd
cd MIDAS_Submission_Prabhav
conda create --name <env> --file requirements.txt
cd Task - 3
```

#### Using Colab

 - Download the Github Repo to your Drive and open a Colab Notebook in the root directory.
 - In the Colab Notebook, 
 ``` python
 !pip install requirements.txt
 !cd Task - 3
```
- Run all notebooks normally.



## Data Preview

- Basic EDA was carried out on the dataset.  Data contained 15 columns and  20003 rows. For the code, only 3 columns were loaded -> Product Name, Product Description, Product Category Tree. Others were ignored as they did not contain any data relevant to the prediction task.

| ![original.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/original.png) | 
|:--:| 
| *Loaded Dataset* |

- While loading dataset, rows with NaN type objects were not loaded and dropped. Product Name and Product Description were concatenated into a new feature column. Simple analysis after this, showed the following results:
```
1. Number of Rows - 20000
2. Number of Columns - product_name, product_description, product_category_tree
3. Unique Categories (Considering each tree as unique category) - 6466
```
- Furthermore, the dataset was higly imbalanced due to the category tree being unique for most products.



## Data Preprocessing Steps and Data Cleaning

### Splitting Category Tree into Levels and Selecting Targets:

 - Each category tree was split into levels. The max number of levels for any tree was seen to be 8.
 - On average, only the first three levels were seen to contain usefull data throughout the dataset.

| ![split.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/split.png) | 
|:--:| 
| *Split of Levels* |


 - Level 1 and Level 2 contained 265 and 218 unique categories repectively. A brief description of both levels is given below.
	- **Level 1** - 265 unique categories. **Mean frequency of each category was only 75. 98% of the data was concentrated in the first 25 categories.**
	- **Level 2** -  218 unique categories. **Mean frequency of each category was only 91. 82% of the data was concentrated in the first 25 categories.**
- Finally, Level 1 and Level 2 were concatenated to form a new product category target. This contained 436 unique categories but the advantage was that, the data was less imbalanced. **84% of the data was in the top 30 categories of the data.**

| ![data1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/data1.png) | 
|:--:| 
| *Top 25 Frequent Categories in Level 1* |

| ![data1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/dtaa12.png) | 
|:--:| 
| *Top 30 Frequent Categories in Level 1 + Level 2* |

Based on this analysis, two target (predicting variables) were selected. Training and testing was performed on both. These are listed below:

	 - Top 25 most frequent categories of Level 1 in the product category tree.
	 - Top 30 most frequent categories of Level 1 + Level 2 (Concatenation) in the product category tree.

### Data Cleaning

The following are the steps for data cleaning:

 - Removal of blank rows.
 - Convert all text to lower case.
 - Remove punctuations using NLTK.
 - Tokenization of each description.
 - Removal of stop words based on NLTK.
 - Application of WordNet Lemmatizer based on three POS Tags:
	 - Adjective
	 - Verb
	 - Adverb

### Data Setup for Training and Testing

As described above, two datasets were created based. A snapshot of both datsets is shown below with their shape:

| ![l1l2.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/l1l2.png) | 
|:--:| 
| *Considered Levels* |
- Dataset 1 (Level 1, Top 25) (19620, 3)
- Dataset 2 (Level 1 + Level 2, Top 30) (16996, 3)

Train - Test Split was 0.85 - 0.15. Furthermore, label encoder was used to make the labels in digitized format.

## Vectorization and Training

For training purposes, a **TF-IDF vectorizer with 15000 features** was used. The reasons for this are:

1.  A word2vec model was also tested. It provided ver similar scores but was discarded due to the large training time and computational expenses. The TF-IDF model performed commensurate to it, in a much less time.
2. A deep learning based model was also tested (GLoVE). A similar trend to the above point was observed.
3. Furthermore, since this is a relatively simpler predictive task, not involving need for context and also based majorly on words related to the category present in description, TF-IDF was a much better fit.

#### Training:

For training, both Naive Bayes and SVM based classifiers were tested. Finally, SVC was selected due to more options in hyperparameter tuning and better relative performance.
The same model was used for both datasets.
Grid CV (Cross Validation) was used for hyperparameter tuning. The details are given below:
```
Parameters Tuned:

C: 1, 10
Gamma: 0, 0.1
Kernel: Linear, RBF

Best Params Returned - {C:10, Gamma:0.1, RBF: 10}

Time Taken To Apply GridCV - 17 minutes 26 seconds
```


## Results and Discussion

#### Summary of Results:

| Dataset | Method Used | Accuracy | Unweighted Recall | Weighted Recall
|--|--|--|--|--|
| Prediction on Top 25 Level 1 Categories | TF-IDF with Hypertuned SVC | 98% | 91% | 98%
| Prediction on Top 30 Level 1 + 2 Categories | TF-IDF with Hypertuned SVC | 98% | 96% | 98%

#### Heatmap of  Both Models:

| ![cmap1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/cmap1.png) | 
|:--:| 
| *Heatmap for predictions on top 25 categories (Level 1)* |

| ![data1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%203/images/cmap2.png) | 
|:--:| 
| *Heatmap for predictions on top 30 categories (Level 1 + Level 2)* |

#### Discussion

We can see that themodel obtains excellent performance on both the dataset configurations. On the model predicting only on Level 1, the model does face some imbalance in classes causing the recall to be lower than what is expected.  The model tends to overfit on the first 10 categories.
On the other hand, the second model performs much better since the dataset reduces in imbalance when 2 levels are combined. 
This is also seen clearly in heatmap 2, wherein, even with more classes, the model performs in a muchmore balanced manner.

## Possible Improvements

1. Use of a biderectional deep learning model like ELMo for better encapsulation of lexical features.
2. Use of oversampling to reduce imbalance in dataset.
3. Topic Modelling to improve recognition of keywords.
