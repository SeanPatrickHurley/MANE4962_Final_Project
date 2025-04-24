Project Name: Fatigue Life Prediction Utilizing Neural Networks

Author: Sean Hurley

Goal:

Use a hybrid neural network to showcase the ability of deep learning to learn highly nonlinear patterns in data with various feature types, particularly when applied to predicting the fatigue life of metal specimens of different alloys. 

Dataset: 

The dataset I used was from the 2024 paper "A deep learning dataset for metal multiaxial fatigue life prediction", specifically the strain controlled data. 

Model: 

The model used is a hybrid neural network, a GRU for the time series data (loading path of the sample) and an ANN for the material type and properties. Both branches are then concatenated together and fed into a final deep neural network, which performs a regression task (the one target being specimen fatigue life). 

Code Instructions: 

First, download the files from the google drive link specified in the "Data_Cleaning_Processing" Jupyter notebook in the "notebooks" folder of the repository. Alternatively, the google drive link is also given in the "data" folder as the text file "google_drive_share_link". If google drive usage is not desirable or otherwise possible, then the requisite files can be found in the "data" folder in the repository as well. 
If google drive is used to load and run the code, either make the following file path "content/drive/MyDrive/MANE4962_FinalProject_RawData/", or change this file path in the code to the folder the files you load the raw data into. 

If issues arise with cleaning and processing the raw data into df_final for testing, the likely issue is running the same cell twice and repeating a column dropping/reindexing. If so, run the second cell (right after drive is mounted), and then each subsequent cell once until you arrive where you started. 

Similar issues may arise when running the training and testing code, since the time series data needs to be reshaped from a flat vector for the GRU component of the Neural Network. Accordingly, run each cell once from the beginning, in order, until you arrive where the issue occurred. 

Summary of Key Findings:

The best results achieved by the model are similar to what is achieved in the paper with ideal hyperparameter tuning and data processing. However, when the model is run multiple times, there is a significant change in the R^2 score, and the percentage of points within the 2x time tolerance. The current proportion is ~50% of points within tolerance, with the highest being 80%. The model has also achieved significantly worse results even with the same hyperparameters. So, the hyperparameters in combination with the very limited number of training epochs (limited to prevent overfitting and plateaus of validation losses), create a model which cannot achieve a reliability accuracy. This means, that rerunning the same model multiple times will result in some models being highly effective, and others much less effective.   