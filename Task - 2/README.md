

# **MIDAS Task 2**

```
Name - Prabhav Singh
Email Id - prabhavs.ic18@nsut.ac.in
```

## Intro

Please go through the file - **[MIDAS_Task2_Explanation.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/MIDAS_Task2_Explanation.pdf "MIDAS_Task2_Explanation.pdf") for an overview of all experiments performed.**
All models, training settings, augmentations etc are defined there.

## Directory Structure

All files present are shown below. Please keep the directory structure the same. A few other points to note are:
1. Make sure to add data files in the folder according to the structure shown below
2. The folder models/ contains all checkoints of models. For naming convention, refer to **MIDAS_Task_2_Explanation.pdf**
3. static/ containsimages used in ReadMe

```
MIDAS_Submission_Prabhav
└── MIDAS_Task_2_Explanation.pdf
└── static
└── models
	└── best.h5
	└── task2_pretrained.h5
	└── task2_retrained.h5
	└── task2_base.h5
	└── task_3_random.h5
	└── task_3_model.h5
└── MIDAS_Task2_Part1.ipynb
└── MIDAS_Task2_Part2.ipynb
└── MIDAS_Task2_Part3.ipynb
```

Screenshot of directory after adding data folders:

| ![main.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/static/main.png) | 
|:--:| 
| *Directory Structure with Data* |

## How to run

#### Using Anaconda
``` cmd
cd MIDAS_Submission_Prabhav
conda create --name <env> --file requirements.txt
cd Task - 2
```

#### Using Colab

 - Download the Github Repo to your Drive and open a Colab Notebook in the root directory.
 - In the Colab Notebook, 
 ``` python
!pip install requirements.txt
!cd Task - 2
```
- Run all notebooks normally.


## Results and Solutions

Please go through the file - **[MIDAS_Task2_Explanation.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/MIDAS_Task2_Explanation.pdf "MIDAS_Task2_Explanation.pdf") for an overview of all experiments performed and discussion of results.**

### Part 1 Results
An overview of basic statistics of results is given below.

|Parameter| Value |
|--|--|
| Accuracy | 90.457% |
| Loss | 0.2599 |
| Convergence | 215 Seconds |

The accuracy and loss graphs are shown below.

| ![Part 1.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/static/Part%201.png) | 
|:--:| 
| *Accuracy and Loss Graphs - Part 1* |

### Part 2 Results

A comparision based result is provide below, comparing both the pretrained and random model on MNIST test set:

| Model | Accuracy | Weighted Recall Avg | Loss | Convergence Time |
|--|--|--|--|--|
| Pretrained | 98% | 98% | 0.318 | 12 min 13 sec |
| Random Init| 98% | 98% | **0.299** | **11 min 47 sec** |

Accuracy and loss plots of both models are compared below. Further, heatmaps are also provided to observe class bias. Discussion is in  **[MIDAS_Task2_Explanation.pdf](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/MIDAS_Task2_Explanation.pdf "MIDAS_Task2_Explanation.pdf")**.

| ![Part 2.png](https://github.com/Prabhav55221/MIDAS_Submission_Prabhav/blob/master/Task%20-%202/static/Part%202.png) | 
|:--:| 
| *Heatmaps, Accuracy and Loss Graphs - Part 2* |


### Part 3 Results

A comparision based result is provide below, comparing both the pretrained and random model on MNIST test set: **One should note, that results are bad due to the incorrectly labelled new dataset provided. This was expected.**

| Model | Accuracy | Weighted Recall Avg | Loss | Convergence Time |
|--|--|--|--|--|
| Pretrained | 0.02% | 0% | 4.56 | **12 min 13 sec** |
| Random Init| 9% | 1% | **2.23** | 16 min 45 sec |

## References

1. ZCA Whitening, Martin Thoma
2. Optimal Window Size for CNNs, Swarnima Pandey
3. Visualisation of Filter Initializers, Pawan SJ
4. A Comparison of Weight Initializers in Deep Learning-based Side-channel Analysis, Li et al., IACR
