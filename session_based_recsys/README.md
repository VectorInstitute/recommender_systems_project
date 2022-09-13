# Recommender Systems

Today, recommendation systems are ubiquitous, spanning sectors as diverse as 


*   online retail,
*   music and video streaming and
*   content publishing.

## Why Recommender Systems matter?

*   We can discover **what's interesting or important** to us among the vast amount of content on the internet. 

*   A recommendation system can assist us in **navigating more efficiently** and making better decisions when it is implemented correctly.

## Different types of Recommender System methods:

There are several types of recommendation systems: **collaborative filtering-based**, **content-based methods**, and **context-aware methods**. 



*   **Collaborative filtering-based:** It refers to the use of interactions between users and items across a number of users to produce recommendations for one particular user based on the preferences of others. Generally, these systems learn users' long-term preferences based on their historical interactions with items (e.g., what they clicked on in the past)

*   **Content-based:** User preferences for product features can be identified either through previous actions or through explicit feedback.

*   **Context-aware methods:** Information related to context, such as location and time, is leveraged.


# Session-Based Recommender Systems

It is almost always the case that choices have a time-sensitive context; for example, some items may be more relevant than others based on **when they were last viewed** or **purchased**.

Despite being embedded in the user's most recent interactions, short-term preferences may only represent a small portion of history. Additionally, a user's preference for certain items can be **dynamic rather than static**; it can evolve over time. 

As a result, **session-based recommendation** algorithms have been developed, which **rely heavily on the user's recent interactions** instead of their historical preferences. Moreover, this approach is especially advantageous since **a user may appear anonymously** if they are not logged in or browsing incognito.  

<p align="center">
<img src="https://session-based-recommenders.fastforwardlabs.com/figures/FF19_Artboard_3rev.png" alt="" style="width:80%;>
</p>


## Benefits of Session-Based Recommender Systems

*   These methods can be implemented even in the **absence of historical user data**, and doesn’t explicitly rely on user population statistics. This is helpful because, as just noted above, users aren’t always logged in when they browse a website.

*   A wealth of new, **publicly available, session-centric datasets** have been released, especially in the e-commerce domain, allowing for model development and research in this area.

*   Session-based recommenders can benefit from the rise of **deep learning approaches** expressly suited for sequences.

## Defining the Session-based Recommender Problem Space

A new customer, has been browsing tops, shoes, and weights. The browsing history looks like this:

<p align="center">
<img src="https://session-based-recommenders.fastforwardlabs.com/figures/FF19_Artboard_4rev.png" alt="" style="width:80%;>
</p>

### What should we recommend to the user next?

**Good recommendations** will **increase the likelihood** that the user will see something they like, click on it, and make a purchase. **Poor recommendations** will, at best, lead to no new revenue, but even worse could give them **a negative customer experience**.


We’ll consider their **recent browsing history** as a **session**. Formally, a session is composed of **multiple user interactions that happen together in a continuous period of time**.

Our goal is to predict the product within user’s session that they will like enough to click on. This task is called **next event prediction (NEP)**: given a series of events (user’s browsing history), we want to predict the next event (user clicking on a product we recommend to them).

<p align="center">
<img src="https://session-based-recommenders.fastforwardlabs.com/figures/FF19_Artboard_5.png" alt="" style="width:80%;>
</p>

In reality, this means that our model might generate a handful of recommendations based on user’s browsing history; we want to **maximize the likelihood** that user clicks on at least one of them. To train a model for this task, we’ll need to use historical browsing sessions from our other existing users to identify trends between products that will help us learn recommendations.

## Notebooks
There are two notebooks in this series of demos that outline the application of session-based recommender systems to the YOOCHOOSE dataset. These demos go from data preproccessing to hyperparameter tuning. In particular, the demos include the following: 

1. **GRU4Rec**: Preprocess YOOCHOOSE dataset, split into train, validation and test sets, and train and evaluate GRU4Rec model on the dataset
2. **NARM**: Preprocess YOOCHOOSE dataset, split into train, validation and test sets, and train and evaluate NARM model on the dataset
