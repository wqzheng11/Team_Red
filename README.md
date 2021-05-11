# Team_Red
DSO 560 Final Project

This repo is created for the final project of DSO 560 Text Analaytics and Natural Language Processing. 

Team Members for Group Red:
Anni Cai | Qiongqiong Lin | Leon Man | Wanqiu Zheng

Project Overview:
Develop a recommendation system that is based on the retail fashion brand's brand descriptive information.

The project includes 2 parts:
1. Build an NLP classification model to predict which brand a new product should be assigned.
   - We created 15 new variables to train the model.
   - We tried RandomForest Classifier, HistGradientBoosting Classifer, AdaBoost Classifier, and KNeighborsClassifier. As a result, we picked HistGradientBoosting        Classifer as the final model, since it achieves a 65.35% average accuracy score through cross validation process.
 
2. Create a brand recommender algorithm that would recommend an outfit given a customer’s search query.
   - We tried both a TFIDF model and a Word2Vec model, and they are documented in TFIDF_Recommendation and Word2Vect_Recommendation files respectively
   - We included a section of future improvements on recommendation algorithm in the TFIDF_Recommendation file

Avaiable Data:
1. Behold Brands
2. Behold Products
3. Outfits and Items
4. Additional Tags

# Abstract

**1.0. X variables we created:**
********************
*   **is_womens_clothing**: bool, 1 - Yes, 0 - NO
*   **is_men_clothing**: bool, 1 - Yes, 0 - NO
*   **origins**: enum, indicate which country a product was produced
*   **Product Categories**: enum, indicate to which product categories (e.g., tops, bottoms and etc.) a product belongs
*   **Colors**: enum, number of colors that a product has 
*   **Materials**: enum, the type of materials by which a product was produced
*   **IS_SLIM_FIT**: bool, 1 - Yes, 0 - NO
*   **IS_RELAX_FIT**: bool, 1 - Yes, 0 - NO
*   **IS_DRY_CLEAN**: bool, 1 - Yes, 0 - NO
*   **model_size**: enum, the size that a brand model was wearing in `description`
*   **product active**: bool, 1 - Yes, 0 - NO
*   **quarter** enum = [1,2,3,4], the number of quarter indicates in which quarter of a year the product was created or more frequent this brand's product was collected by Behold
*   **product_creation_speed** float, the number indicates the rank of velocity of product creation, the lower the rank, the faster a brand will launch its clothing prducts
*   **product_description embedding**: embedding size = 200
*   **brand_name doc2vec embedding**: embedding size = 6 
*   **Flesh-Kincaid Grade of `brand_name` and `product_descr`**: float, indicates the readability of `product descr` and `brand_name`. The higher the value, the more complex the document to read
*   **Gunning-Fog Grade of `brand_name` and `product_descr`**: float, indicates the readability of `product descr` and `brand_name`. The higher the value, the more complex the document to read

**2.0. Data Cleaning:**
********************
- For categorical variables (variable type: enum), one-hot encoding was applied to create dummy variables
- new new line character `\n` will be removed from the entire dataset 
- Stopwords removal and lemmatization will be conducted on `brand_name` and `product_descr` for doc2vec. However, for calculating `Flesh-Kincaid` and `Gunning-Fog`, these operations are needed. The reason why we conducted text cleaning before doc2vec embedding is the explanatory power of models were improved after removing stopwords and punctuations from them.

**3.0. Y variables:**
********************
*   We group the most frequent 50 brands and classify the remaining others as `Others`
*   Therefore, our benchmark is 15%, and optimal threshold is 50%

**4.0. Models:**
********************
The reason why we prefer tree-based models are 1) Tree-based models are robust to variables with different scale. People do not have to normalize data to make it work in a high dimension space. 2) Tree-base models can tell us which predictors have the highest informmation gain. This will be critical for fine-tuning our models. 3) tree-based is also robust to high dimension datasets. Even if we did not perform dimensionality reduction, it can still achieve expected performance. For those variables with low predictive power, tree-based models will simply put them on the sideline and do not use them to make splits. 4) tree-base models are fast to train than most other models in our experimentation.

*   **Random Forest Classifier**: oob_score is surprisingly high. Maybe cross validation can reveal its true performance
*   **Hist Gradient Boosting Classifer**: the best model based on the testing set, but it's slow to train
*   **Ada Boost Classifier**: the model didn't perform well on the testing set, would not take into further consideration.
*   **KNeighbors Classifier**: did a fair job on the testing set, could be an option to go for

**5.0. Our final pick of the model**
********************
Hist Gradient Boosting Classifer: it delivers the best performance throughout cross validation process, also it is much faster to train than RNN model. The average accuracy score for Hist Gradient Boosting Classifer is 70.4%. Please note the cross validation of `Hist Gradient Boosting Classifer` will be very slow.















