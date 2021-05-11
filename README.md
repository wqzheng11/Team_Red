# Team_Red
DSO 560 Final Project

This repo is created for the final project of DSO 560 Text Analaytics and Natural Language Processing. 

Team Members for Group Red:
Anni Cai | Qiongqiong Lin | Leon Man | Wanqiu Zheng

Project Overview:
Develop a recommendation system that is based on the retail fashion brand's brand descriptive information.

The project includes 2 parts:
1. Build an NLP classification model to predict which brand a new product should be assigned.
   - We created 17 new variables to train the model.
   - We tried RandomForest Classifier, HistGradientBoosting Classifer, AdaBoost Classifier, and KNeighborsClassifier. As a result, we picked HistGradientBoosting        Classifer as the final model, since it achieves a 65.35% average accuracy score through cross validation process.
 
2. Create a brand recommender algorithm that would recommend an outfit given a customer’s search query.
   - We tried both a TFIDF model and a Word2Vec model for the search function, and they are documented in TFIDF_Recommendation and Word2Vect_Recommendation files respectively
   - We included a section of future improvements on recommendation algorithm in the TFIDF_Recommendation file

Avaiable Data:
1. Behold Brands
2. Behold Products
3. Outfits and Items
4. Additional Tags
