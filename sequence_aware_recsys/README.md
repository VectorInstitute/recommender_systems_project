## Introduction to Sequence Aware Recommender Systems
Traditional recommender system methods such as matrix factorization assume static preference of users. However, users preferences often evolve over time based on their past interactions. For example, it is reasonable to assume that users who purchase an iPhone on Amazon are more likely to purchase products such as phone cases and chargers in the future. This implies there is inherent value in modelling the temporal dynamics of user interactions. In general, sequential interaction data of a user takes the following form: 

<p align="center">
<img width="818" alt="image" src="https://user-images.githubusercontent.com/34798787/182863761-6f195aa8-7a73-4abb-a440-5debf1cb44fb.png">
</p>

In the recommender system literature, there are two overlapping classes of approaches that model sequence of user interactions: sequence aware recommender systems and session based recommender systems. The distinction between the approaches lies in the data. Sequence Aware Recommender systems have sequences of interaction for a set of known users. This sequence of interactions exists across one or more sessions. Alternatively, Session-Based recommender systems have sequences of interactions for an uknown set of users. Thus, there is no concept sequences existing across sessions. 

<p align="center">
<img width="956" alt="image" src="https://user-images.githubusercontent.com/34798787/182865897-b2ff207f-111d-4716-a809-3682009abf2c.png">
</p>

The topic of this demo is sequence aware recommender systems. In general, sequence aware recommender systems start by generating embeddings for each interaction in a given sequence. This involves mapping the continuos and categorical variables of each interaction to an embedding using embedding tables or Multi Layer Perceptrons (MLP). This results in a sequence of embeddings that is then fed into a Neural Network model that predicts the probability distribution over items given their previous interactions. The neural network can be chosen to have different architectures. Typically, Recurrent Neural Network (RNN) or Transformers are used because their success with sequential data. 

<p align="center">
<img width="977" alt="image" src="https://user-images.githubusercontent.com/34798787/182866390-4e1322b5-2d68-4dd2-ad5f-f1814a965b95.png">
</p>

## Dataset
In this series of demos we will explore the [Amazon Review Dataset](https://nijianmo.github.io/amazon/index.html). This dataset includes reviews (ratings, text, helpfulness votes), product metadata (descriptions, category information, price, brand, and image features), and links (also viewed/also bought graphs). This version provides 233.1 million reviews in total and additonal metadata. The reviews are distributed across 26 high level groups, as illustrated below: 

<p align="center">
<img width="600" alt="Amazon categories" src="https://user-images.githubusercontent.com/34798787/177803504-89909b59-a2cd-497b-b892-64f40a9a9e29.png">
</p>

We will specifically be looking at the Movies and TV category - which is commonly used as a benchmark in the recommender system literature. The data is processed and stored in a table where each row contains the features and label of a single interaction. The features include user id, item id, category id and the timestamp of the interaction. The label is binary indicating whether a review exists between that specific user-item pair. 

## Notebooks
There are several notebooks in this series of demos that outline the application of sequence aware recommender systems to the Amazon review dataset. These demos go from data preproccessing to hyperparameter tuning. In particular, the demos include the following: 

1. **amazon_preprocessing**: Download amazon data, preprocess and split into train, validation and test sets.
2. **a2svd**: Train and evaluate baseline non-sequential recommender system method Asymmetric SVD (a2SVD)
3. **slirec**: Train and evaluate sequential recommender system method Short-term and Long-term preference Integrated Recommender system (SLi-Rec)

## Environment Configuration 
From the current directory of the repo, run the following commands:
```
conda create -n recsys python=3.7
conda activate recsys 
pip install -r requirements.txt
```


