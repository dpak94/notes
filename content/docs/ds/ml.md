---
type: "docs"
title: Machine Learning
draft: true
url: "/docs/ds/machine-learning/"
---

# Machine Learning Notes

## AI vs ML vs DL

| Artificial Intelligence                                                                                                                                                                                                   | Machine Learning                                                                                                                                                                                                                                                                                         | Deep Learning                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AI stands for Artificial Intelligence, and is basically the study/process which enables machines to mimic human behaviour through particular algorithm.                                                                   | ML stands for Machine Learning, and is the study that uses statistical methods enabling machines to improve with experience.                                                                                                                                                                             | DL stands for Deep Learning, and is the study that makes use of Neural Networks(similar to neurons present in human brain) to imitate functionality just like a human brain.                                                                                           |
| AI is the broader family consisting of ML and DL as it’s components.                                                                                                                                                      | ML is the subset of AI.                                                                                                                                                                                                                                                                                  | DL is the subset of ML.                                                                                                                                                                                                                                                |
| AI is a computer algorithm which exhibits intelligence through decision making.                                                                                                                                           | ML is an AI algorithm which allows system to learn from data.                                                                                                                                                                                                                                            | DL is a ML algorithm that uses deep(more than one layer) neural networks to analyze data and provide output accordingly.                                                                                                                                               |
| The aim is to basically increase chances of success and not accuracy.                                                                                                                                                     | The aim is to increase accuracy not caring much about the success ratio.                                                                                                                                                                                                                                 | It attains the highest rank in terms of accuracy when it is trained with large amount of data.                                                                                                                                                                         |
| Three broad categories/types Of AI are: Artificial Narrow Intelligence (ANI), Artificial General Intelligence (AGI) and Artificial Super Intelligence (ASI)                                                               | Three broad categories/types Of ML are: Supervised Learning, Unsupervised Learning and Reinforcement Learning                                                                                                                                                                                            | DL can be considered as neural networks with a large number of parameters layers lying in one of the four fundamental network architectures: Unsupervised Pre-trained Networks, Convolutional Neural Networks, Recurrent Neural Networks and Recursive Neural Networks |
| The efficiency Of AI is basically the efficiency provided by ML and DL respectively.                                                                                                                                      | Less efficient than DL as it can’t work for longer dimensions or higher amount of data.                                                                                                                                                                                                                  | More powerful than ML as it can easily work for larger sets of data.                                                                                                                                                                                                   |
| **Examples:** Google’s AI-Powered Predictions, Ridesharing Apps Like Uber and Lyft, Commercial Flights Use an AI Autopilot, etc.                                                                                          | **Examples :** Virtual Personal Assistants: Siri, Alexa, Google, etc., Email Spam and Malware Filtering.                                                                                                                                                                                                 | **Examples :** Sentiment based news aggregation, Image analysis and caption generation, etc.                                                                                                                                                                           |
| AI refers to the broad field of computer science that focuses on creating intelligent machines that can perform tasks that would normally require human intelligence, such as reasoning, perception, and decision-making. | ML is a subset of AI that focuses on developing algorithms that can learn from data and improve their performance over time without being explicitly programmed.                                                                                                                                         | DL is a subset of ML that focuses on developing deep neural networks that can automatically learn and extract features from data.                                                                                                                                      |
| AI can be further broken down into various subfields such as robotics, natural language processing, computer vision, expert systems, and more.                                                                            | ML algorithms can be categorized as supervised, unsupervised, or reinforcement learning. In supervised learning, the algorithm is trained on labeled data, where the desired output is known. In unsupervised learning, the algorithm is trained on unlabeled data, where the desired output is unknown. | DL algorithms are inspired by the structure and function of the human brain, and they are particularly well-suited to tasks such as image and speech recognition.                                                                                                      |
| AI systems can be rule-based, knowledge-based, or data-driven.                                                                                                                                                            | In reinforcement learning, the algorithm learns by trial and error, receiving feedback in the form of rewards or punishments.                                                                                                                                                                            | DL networks consist of multiple layers of interconnected neurons that process data in a hierarchical manner, allowing them to learn increasingly complex representations of the data.                                                                                  |

---

## Some ML Terminology

### Precision & Recall

- Precision describes how many retrieved items are relevant.
- Recall gives how many relevant items are retrieved.

---

## Scaling in ML

**Feature scaling** is the process of normalizing the range of features in a dataset. Real-world datasets often contain features that are varying in degrees of magnitude, range, and units. Therefore, in order for machine learning models to interpret these features on the same scale, we need to perform feature scaling.

**Types of Scalar Functions :**
A. MinMaxScalar() Function
B. StandardScaler Function
C. RobustScaler Function

### MinMaxScaler() Function

Transform features by scaling each feature to a given range. This estimator scales and translates each feature individually such that it is in the given range on the training set, **e.g.** between zero and one.

**Scikit Learn Syntax :** ==from sklearn.preprocessing import MinMaxScaler==

### StandardScaler() Function

Standardize features by removing the **mean** and scaling to **unit variance**. The standard score of a sample x is calculated as:

$$
z = (x - u) / s
$$

**Scikit Learn Syntax :** ==from sklearn.preprocessing import StandardScaler==

### RobustScaler Function

Scale features using statistics that are robust to outliers.

This Scaler removes the median and scales the data according to the quantile range (defaults to **IQR: Interquartile Range**). The IQR is the range between the 1st quartile (25th quantile) and the 3rd quartile (75th quantile).

Centering and scaling happen independently on each feature by computing the relevant statistics on the samples in the training set. Median and interquartile range are then stored to be used on later data using the transform method.

Standardization of a dataset is a common requirement for many machine learning estimators. Typically this is done by removing the mean and scaling to unit variance. However, outliers can often influence the sample mean / variance in a negative way. In such cases, the median and the interquartile range often give better results.

**Scikit Learn Syntax :** ==from sklearn.preprocessing import RobustScaler==

---

## Ensemble Algorithms

### Bagging Method

In this method, a random sample of data in a training set is selected with replacement—meaning that the individual data points can be chosen more than once. After several data samples are generated, these models are then trained independently, and depending on the type of task—i.e. regression or classification—the average or majority of those predictions yield a more accurate estimate.

This approach is commonly used to reduce variance within a noisy dataset.

### Random Forest Method

![Random Forest](https://www.ibm.com/content/dam/connectedassets-adobe-cms/worldwide-content/cdp/cf/ul/g/50/f9/ICLH_Diagram_Batch_03_27-RandomForest.component.xl.ts=1679336476850.png/content/adobe-cms/us/en/topics/random-forest/jcr:content/root/table_of_contents/body/content_section_styled/content-section-body/simple_narrative0/image)

The random forest algorithm is an extension of the bagging method as it utilizes both bagging and feature randomness to create an uncorrelated forest of decision trees.

**Applications :**

- **Finance :** Preferred algo over others as it reduces time spent on data management and pre-processing tasks. It can be used to evaluate customers with high credit risk, fraud detection and option pricing problems.
- Gene expression classification, biomarker discovery, sequence annotation, estimating drug responses to specific medications.
- **E-commerce :** It can be used for recommendation engines for cross-sell purposes.

---

## Learning Algorithms - Types of Learning

1. Supervised Learning
2. Clustering
3. Reinforcement Learning

## Supervised Learning

- Algorithms designed to learn by example
- Models are trained on **well-labeled** data
- Each training example is a pair consisting of :
  - **Input** Object (typically a vector)
  - **Desired** Output (Supervisory Signal)
- During training, **Supervised Learning** Algorithm searches for patterns that correlate with the desired output
- After training, it takes in unseen inputs and determine which label to classify it to
- Supervised Learning is of two types:
  - **Classification**
  - **Regression**

### Classification

In classification, input data is taken and assigned to a class/category

**Example :** Classification of e-mails as spam or not spam

Models find features in the data that correlate to a class and creates a **Mapping Function**. This mapping function will be used to classify unseen data.

**Popular Classification Algorithms**

- Linear Classifiers
- Support Vector Machines
- K-Nearest Neighbour
- Random Forest

### Regression

Model attempts to find a relationship between dependent & independent variables. The goal is to predict continuous values such as test scores, stock prices etc.

**Popular Regression Algorithms**

- Linear Regression
- Lasso Regression
- Multi-Variate Regression

## Unsupervised Learning

- Uses to manifest **underlying patterns** in data
- Used in exploratory data analysis
- Does not use labelled data, rather relies on the **data features**
- **Goal** is to analyze data and find important underlying patterns

Types of Unsupervised Learning:

- Clustering
- Association

### Clustering

Process of grouping data into different groups or clusters.The goal s to predict continuous values such as test scores

**A. Partitional Clustering**
Each data point can belong to a single cluster
**B. Hierarchical Clustering**
Clusters within clusters
Data point may belong to many clusters

Popular Clustering Algorithms

- **K-Means**
- **Expectation Maximization**
- **Hierarchical Cluster Analysis (HCA)**

### Association

Attempts to find relationships between different entities
**Example** Market Basket Analysis

---

## Reinforcement Learning

**Reinforcement Learning** is a machine learning training method based on rewarding desired behaviors and punishing undesired ones. In general, a reinforcement learning agent -- the entity being trained -- is able to perceive and interpret its environment, take actions and learn through trial and error.

**Example**
Maximize the points won in a game over many moves, Chess Game etc.

- **Penalize** when wrong decisions are made
- **Reward** when right decisions are made

This is known as **Markov Decision Process**

**Applications**

- Robotics
- Business Strategy Planning
- Traffic Light Control
- Web System Configuration

---
