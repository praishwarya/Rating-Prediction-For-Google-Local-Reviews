# Rating-Prediction-For-Google-Local-Reviews

Instructions to Run:
- Dataset available in the "data" directory
- First, run the Data_Processing.ipynb to generate filtered and cleaned data pickle files to be used as inputs for the models
- Latent_Factor_Models.ipynb contains the simple linear Latent Factor models, Factorization Machines and Factored Item Similarity Model
- Linear_Regression_XG_Boost.ipynb contains the Linear Regression and XGBoostRegressor decision tree models

To install FastFM module, run the following commands in your machine:
# !git clone --recursive https://github.com/ibayer/fastFM.git
# import os
# os.chdir("./fastFM/")
# !pip install -r ./requirements.txt
