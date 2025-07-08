# Rating-Prediction-For-Google-Local-Reviews

[Google Local Reviews (2018) Dataset](https://cseweb.ucsd.edu/~jmcauley/datasets.html#:~:text=Google%20Local%20Reviews%20(2018))
- Create a "data" directory under the project root
- Download the "users.clean.json.gz", "reviews.clean.json.gz" and "places.clean.json.gz" files from the above link
- Copy the downloaded json.gz files into the "data" directory

Instructions to Run:
- First, run the "Data_Processing.ipynb" to generate filtered and cleaned data pickle files to be used as inputs for the models
- "Latent_Factor_Models.ipynb" contains the simple linear Latent Factor models, Factorization Machines and Factored Item Similarity Model
- "Linear_Regression_XG_Boost.ipynb" contains the Linear Regression and XGBoostRegressor decision tree models

To install FastFM module, run the following commands in your machine:
- !git clone --recursive https://github.com/ibayer/fastFM.git
- import os
- os.chdir("./fastFM/")
- !pip install -r ./requirements.txt
