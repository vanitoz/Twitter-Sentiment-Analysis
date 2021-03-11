# Sentiment Analysis on Twitter. Hate Speech recognition

![Blight]


## Overview
Labeled racist, sexist, and homophobic tweets


## Business Problem
In our modern world we have freedom in sharing our thoughts, beliefs, criticizing other people and commenting their thoughts on different social media. It became possible also due to growing democracy both in the structure of different countries and in the use of social networks and the dissemination of people’s opinions through them.
Moreover, some individuals feel that it is natural to use hate speech with regard to other people on social media, but it is not respectful and polite towards persons who get this comments or who can simply notice this text with inappropriate vocabulary during scrolling other tweets. We can identify hate speech as injurious or undermining speech that communicates preference against a specific cluster, particularly on the premise of race, religion or sexual orientation.
Additionally, natural use of hate speech grows the culture of using impolitic vocabulary between new generations Z and Y.
Shockingly, each major tech company, counting Twitter, hires human mediators to a few degrees, both locally and abroad. Most of the social media platforms still don’t have moderate speech instruments which can automatically identify and correct hate speech or ban it and prevent the text with it from being published.


## Approach

General Approach for this problem was based on Cross Industry Standard Process for Data Mining (CRISP-DM)
Which includes all following pmpotrtant steps: 

1. Look at the big picture. 
2. Get the data. 
3. Discover and visualize the data to gain insights. 
4. Prepare the data for Machine Learning algorithms. 
5. Select a model and train it. 
6. Fine-tune your model. 
7. Present your solution. 
8. Launch, monitor, and maintain system.

<p align="center">
    <img src="images/approach.png" alt="drawing" width="500" hight="200"/>
    
## Methodology

Based on our business problem we are trying to accomplish certain tasks that involve natural language. NLP allows computers to interact with text data in a structured and sensible way. With NLP, computers are taught to understand human language, its meaning and sentiments. In order to translate complex natural human language into systematic constructed features we need to follow some major steps which showed on the next graph.

<p align="center">
    <img src="images/NLP_protcess.png" alt="drawing" width="600" hight="300"/>



## Analysis

Data for this project was soursed from a study about Automated Hate Speech Detection and the Problem of Offensive Language conducted by team of Cornell University in 2017. Aditional data sourse from Association for Computational Linguistics provide us labeled data with tweets ID's that contain hate speech. Links to data sourses can be finded in references below.

During EDA we discovered that data from Cornell University appears to be inbalanced with minority class as hate speech and represented on a left side of the graph. After API requests with labeled as hate speech tweets ids we were able to bring more data to our project and balance it. Left side of the graph shows balanced data.
 

<img src="images/class_inbal.png" width="500"/> <img src="images/class_balan.png" width="500"/>
 
After appropriate Pre-Protcesing that include Tokenization, Remowing Stop-words and Cleaning Data we were able to generate freequency distribution of words within whole corpus. It helped to understand data better and explained to us what kind of additional cleaning needs to be done before turn data into  Docunent-Term Matrix. Graph below shows 25 most freequent words that we were able to find in each class that belong to main corpus.

<p align="center">
    <img src="images/word_count_graphs.png" alt="drawing" width="900" hight="600"/>

With WordCloud library we were able to create bags of most imporatnt words in each class. We also observed that both classes has lots of the same words that located in corpus of our data. Because of the similarities of each label’s vocabulary, it could be difficult for machine learning algorithms to differentiate between them and determine what counts as hate speech.

<p align="center">
    <img src="images/clouds.png" alt="drawing" width="900" hight="500"/>

With fruther analyzys we were able to find out and create vocabluary of only words that belong to tweets labeled as hate speech. We found 6312 words that exclusivly belong to tweets labeled as hate speech. Majority of hate speech words are racist, sexist and homophobic slurs that exceed cultural slang. The fact that these words are unique to the "Hate Speech" label affirm that it's indeed hate speech that should be flagged and taken down.


<p align="center">
    <img src="images/venn.png" alt="drawing" width="600" hight="300"/>

Graph above represents venn diagram that show how many unique words belong to each class and how many words showing up in both classes. 3391 words showing up in both classes which makes difficult for machine learning model to predict correct lable on particular tweets.
After futers engeneering with TF-IDF Vectorization the next step take place for creating models and evaluate them.


## Modeling

F1 score and Recall was used as main evaluation metrics for this project. We want to classify correct hate speech as much as possible and so that it can be efficiently removed. 
Starting with base line models, Random Forest, Naive Bayes, Logistic Regression was applied to inbalance data. Best result was shown by Random Forest Model with Recall = 12% and F1-score = 19%

Next step was to run the same 3 models on ballanced data. Following table shows perfomance of each model on test set.

<p align="center">
    <img src="images/results.png" alt="drawing" width="500" hight="250"/>
 
Based on results, the heighest Recall and F-1 score acchived with Random Forest and Naive Bayes classifier. Following step was to use GridSearch with Random Forest classifier to get best parameters in order to achive higer Recall score. Random Forest with Hyper Parameters selected with GridSearch let us create final model with following results on testing data: 
Precision: 0.7124
Recall: 0.937
Testing Accuracy: 0.7816
F1 Score: 0.8094

Confusion Matrix below explain high True Positive rate. In this business context, we would ideally want as many True Positives as possible, because that would be identifying Hate Speech correctly.

<p align="center">
    <img src="images/matrix.png" alt="drawing" width="350" hight="350"/>

## Conclusion



## Future Work




## Repository Structure

    ├── README.md                    # The top-level README for reviewers of this project"
    ├── data                         # Synergized Data obtained from University of Michigan and Detroit Open Data Portal"
    ├── modules                      # py files with functions for ingeniring and modeling"
    ├── images                       # Both sourced externally and generated from Code"       
    ├── modeling.ipynb               # Notebook that gpes pver out modling process"                                        
    └── features_engineering.ipynb    # Notebook Used for feature engineering before Modeling"
    
    
**Authors** <br>
[Ivan Vanko](https://github.com/vanitoz)<br>
[Kelvin Arellano](https://github.com/Kelvin-Arellano)<br>
