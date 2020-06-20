![header](./src/header.jpg)

### Objective

Code Kata is defined as an **exercise** in programming which helps hone our skill through **practice and repetition**. In machine learning programming, Code Kata for implementing **ML algorithms** is very important, becuase we can realize the details ( such as Data Sampling, Weight initialization, various Training Strategy ...) while implementing the algorithm. 

I implement various algorithms that make up the recommendation system and organize them into scripts.



### How to do the Code Kada together? (set-up environment)

Do not worry! I provide the environment written as a [docker image](https://hub.docker.com/repository/docker/craftsangjae/jupyter-dojo).

````shell
# Run it From the root project directory
docker-compose up -d
````



### Rec-Sys Katas List



----

#### [Mining-Frequent-Pattern(apriori)-using-pandas]

**Goals**

1. Implement Apriori function to extract frequent itemsets

2. Implement function to generate association rules from frequent itemsets

**Reference**

* [mlxtend](http://rasbt.github.io/mlxtend/user_guide/frequent_patterns/association_rules/)

---

#### [Thompson Sampling For A/B Test]

**Goals**

* Implement Thompson Sampling Agent to find best choice for A/B Test.



----

#### [Real-Time Collaborative Filtering using MinHash]

**Goals**

* Implement Item-based CF Algorithm perfoming real-time recommendations and real-time Updates.
* two Ideas Included : (Below ideas were presented by YongHo-Ha)
  * Minhash as a LSH 
  * Secondary Indexing

**Reference** 

* [YongHo-Ha's Recommender System Design](https://www.slideshare.net/deview/261-52784785)



----

#### [Bayesian Personalized Ranking with Tensorflow]

**Goals**

* Implement BPR Algorithms (a kind of Matrix Factorization for implicit datasets)  using Tensorflow

**Reference** 

* [github - implicit](https://github.com/benfred/implicit)



----

#### [Serving Matrix Factorization using Annoy]

**Goals**

* perform item-based recommendation using approximate nearest neighbor search

**Reference**

* [github - annoy](https://github.com/spotify/annoy)



---

#### [Nueral Collaborative Filtering With Tensorflow]

**Goals**

* Implement NCF Models introduced in the [NCF Paper](https://arxiv.org/abs/1708.05031)

**Reference**

* [author's implementation](https://github.com/hexiangnan/neural_collaborative_filtering)



---

#### DeepFM using Tensorflow

**Goals**

* Implement NCF Models introduced in the [DeepFM Paper](https://arxiv.org/pdf/1703.04247.pdf)

**Reference**

* [paper - DeepFM](https://arxiv.org/pdf/1703.04247.pdf)





#### CopyRight

