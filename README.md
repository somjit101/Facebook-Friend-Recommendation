# Facebook-Friend-Recommendation
This is a friend recommendation system used on social media platforms (e.g. Facebook, Instagram, Twitter) to suggest friends/new connections based on common interests, workplace, common friends etc. using Graph Mining techniques. Here, we are given a social graph, i.e. a graph structure where nodes are individuals on social media platforms and a directed edges (or 'links') indicates that one person 'follows' the other, or are 'friends' on social media. Now, the task is to predict newer edges to be offered as 'friend suggestions'. 


## Problem Statement
**Given a directed social graph, have to predict missing links to recommend users.** (Link Prediction in Graph)

### Data Overview
[Dataset Link](https://www.kaggle.com/c/FacebookRecruiting/data)

Taken data from facebook's recruting challenge on [Kaggle](https://www.kaggle.com/c/FacebookRecruiting)
Data contains two columns source and destination eac edge in graph.
* Data columns (total 2 columns):  
    - source_node         int64  
    - destination_node    int64  

### Mapping the problem into supervised learning problem:
* Generated training samples of good and bad links from given directed graph and for each link got some features like no of followers, is he followed back, page rank, katz score, adar index, some svd fetures of adj matrix, some weight features etc. and trained ml model based on these features to predict link. 

* Some reference papers and videos :  
    - [The Link Prediction Problem for Social Networks](https://www.cs.cornell.edu/home/kleinber/link-pred.pdf)
    - [New Perspectives and Methods in Link Prediction](https://www3.nd.edu/~dial/publications/lichtenwalter2010new.pdf)
    - [Network Analysis Lecture](https://www.youtube.com/watch?v=2M77Hgy17cg)


### Real-world Objectives and Constraints
* No low-latency requirement.
* Probability of prediction is useful to recommend ighest probability links

### Performance metric for supervised learning:  
* Both precision and recall is important so F1 score is good choice
* Confusion matrix

## Solution Approach

Decision Tree based approached proved to be quite effective for this problem statement and since the number of features constructed is not too large, bagging and boosting approaches could be easily employed for high precision and easy training. 

Here are the details and performance metrics of the classifiers used : 

| **Model** | **No. of Base Learners** | **Max Depth of Base Learners** | **Training F1-score** | **Testing F1-score** |
| --------- | ------------------------ | ------------------------------ | --------------------- | --------------------- |
| Random Forest | 121                  | 14                             | 0.964                 | 0.921                |
|    XGBoost    | 109                  | 10                             | 0.992                 | 0.926                 |
