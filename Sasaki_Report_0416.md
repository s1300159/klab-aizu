T0.1  
Setup

I set up the environment on a Windows PC with a GPU.

I used Python to create a virtual environment and conducted the experiment within that environment.  
First, I installed Python, created a virtual environment, cloned the repository, and installed the required libraries.

The environment used in this experiment is as follows:

OS: Ubuntu 22.04 (via WSL2)  
Python: 3.10  
Library: BindsNET  
Environment name: myenv  
Using the Scripts

In this experiment, I used a subset of the MNIST dataset for training and evaluation.  
Originally, 6000 images are used, but due to time constraints, I reduced the dataset to 250 images.

To perform model merging, I prepared four sub-models, each trained on 250 images.

Experimental Settings  
Number of images per model: 250  
Number of models: 4  
Number of neurons: 50  
Results

After training each model, I evaluated their performance and then applied the merging process.

Accuracy before merging (average): 0.4204  
Accuracy after merging: 0.4301

The accuracy slightly improved after merging. However, the improvement was limited due to the small number of training images.

Plot Results

The following figures show the visualization of receptive fields after training.

Discussion

From the plot results, it can be observed that neurons respond to specific patterns.  
Some neurons appear to capture features such as the outlines of digits.

However, due to the small dataset size, some neurons did not learn clear features.  
This is likely caused by insufficient training data.

In addition, the improvement after merging was limited, suggesting that using a larger dataset would lead to better performance.

Commands Used  
Training  
python eth\_mnist\_train.py \--model\_number 1 \--n\_neurons 50 \--start\_image 0 \--end\_image 250  
python eth\_mnist\_train.py \--model\_number 2 \--n\_neurons 50 \--start\_image 250 \--end\_image 500  
python eth\_mnist\_train.py \--model\_number 3 \--n\_neurons 50 \--start\_image 500 \--end\_image 750  
python eth\_mnist\_train.py \--model\_number 4 \--n\_neurons 50 \--start\_image 750 \--end\_image 1000  
Testing  
python eth\_mnist\_test.py \--model\_number 1 \--n\_neurons 50 \--start\_image 0 \--end\_image 250  
python eth\_mnist\_test.py \--model\_number 2 \--n\_neurons 50 \--start\_image 250 \--end\_image 500  
python eth\_mnist\_test.py \--model\_number 3 \--n\_neurons 50 \--start\_image 500 \--end\_image 750  
python eth\_mnist\_test.py \--model\_number 4 \--n\_neurons 50 \--start\_image 750 \--end\_image 1000  
Merging  
python3 eth\_mnist\_merge.py \--method mse \--n\_compression 50  
Plotting  
python eth\_mnist\_plot.py \--model\_number 1 \--n\_neurons 50 \--start\_image 0 \--end\_image 250  
Notes

The receptive field visualizations help to understand how neurons learn features from input data.