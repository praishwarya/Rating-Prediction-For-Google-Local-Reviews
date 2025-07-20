# Factorization Machines to predict rating for Google Local Reviews

In this work, we consider the Google Local reviews dataset since it consists of data from a large variety of businesses ("items"). The reviews dataset consists of user reviews of businesses and the associated user and business metadata. The significant sparsity (few interactions per user) makes it challenging because it is difficult to gauge the user’s preferences. The data is contained in three files - User Data(4,567,431 entries), Places Data (3,116,785 entries) and Review Data(11,453,845 entries). 

## Dataset Information: 
The dataset used is https://cseweb.ucsd.edu/~jmcauley/datasets.html#:~:text=Google%20Local%20Reviews%20(2018) 

The following fields are present:
1. User Data
- userName - Name of the user(String)
- jobs - A list describing the job history of the user including organization, start date and end date
- currentPlace - The user’s current location (includes city, state and GPS coordinates)
- previousPlaces: A list of the user’s past locations (includes city, state and GPS coordinate)
- education - A list describing the educational history of the user including institute, start date and end date
- gPlusUserId - A string which is unique to each user
2. Places Data
- name - Name of the business
- price - One of ‘’, None, $, $$, $$$
- address - As a list of strings
- hours - As a list of Weekday and Timing
- phone - String denoting the phone number
- closed - String indicating whether the place is closed
- gPlusPlaceID - A string which is unique to each place
- gps - A latitude and longitude tuple
3. Review Data
- rating - A 0 to 5 rating for the business by a user
- reviewerName - String indicating the user’s name
- reviewText - String with the user’s review of the business
- categories - A list of strings specifying the category of the business
- gPlusPlaceId - ID of the business
- unixReviewTime - The unix timestamp of the review
- reviewTime - The date in MMM DD YYYY (MMM is first three letters of the month)
- gPlusUserId - This is the user ID of the user who gave the rating

## Code Information and Usage Instructions:
- Create a "data" directory under the project root
- Download the "users.clean.json.gz", "reviews.clean.json.gz" and "places.clean.json.gz" files from the above link
- Copy the downloaded json.gz files into the "data" directory
- First, run the "Data_Processing.ipynb" to generate filtered and cleaned data pickle files to be used as inputs for the models
- "Latent_Factor_Models.ipynb" contains the simple linear Latent Factor models, Factorization Machines and Factored Item Similarity Model
- "Linear_Regression_XG_Boost.ipynb" contains the Linear Regression and XGBoostRegressor decision tree models

To install FastFM module, run the following commands in your machine:
- !git clone --recursive https://github.com/ibayer/fastFM.git
- import os
- os.chdir("./fastFM/")
- !pip install -r ./requirements.txt

## Requirements:
- python==3.10.10
- numpy==1.26.4
- scipy==1.10.1
- fastFM==0.2.10
- pandas==2.0.1
- xgboost==3.0.2
- basemap==2.0.0
- basemap_data==2.0.0
- scikit-surprise==1.1.4

## Methodology: 
The original dataset contains data about businesses and reviews from all around the world. Since processing this huge amount of data will be computationally expensive (considering the limited hardware we are working with), we filtered it to include only people, places and reviews from only the USA. We also consider a subset of the dataset with more interactions per user. 

In addition, the following filtering was done:
- Businesses which have ’None’ or ‘’ for the price field were removed
- There are 145149 categories of businesses. We filtered out the top 50 categories and their distribution is shown in Figure 2. As you can see, the dataset is dominated by reviews from a few categories (mostly different types of restaurants)

After cleaning the data, we are left with 749,000 entries for the review data, which we then split to Train, Validation and Test sets. Further for the training set we filtered out multiple users who only had a single review. Our final dataset consists of 532,880 samples, with the train, validation and test sets in the ratio 70%/20%/10%

## Citations: 
- Translation-based factorization machines for sequential recommendation <br>
Rajiv Pasricha, Julian McAuley <br>
RecSys, 2018
- Translation-based recommendation <br>
Ruining He, Wang-Cheng Kang, Julian McAuley <br>
RecSys, 2017
