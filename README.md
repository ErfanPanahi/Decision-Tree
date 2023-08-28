# Decision-Tree
In this repository, I intend to implement a decision tree algorithm. Subsequently, I will focus on enhancing a section of the decision tree algorithm and utilizing random forests.

In this project, the aim is to implement the decision tree algorithm without using ready-made libraries, using the provided data.

    Import pandas as pd
    Train = pd.read_csv(“titanic-train.csv”)
    Test = pd.read_csv(“titanic-test.csv”)

Titanic Ship Data: From the dataset named "train-data.csv," we select 80% as training data and 20% as testing data. To achieve this, we utilize the `train_test_split` function from the `sklearn.model_selection` library.

The aim is to predict the survival or non-survival of individuals on board the Titanic by utilizing their personal characteristics.

**Part A:** Implementation of Decision Tree Model
Effective Features in Titanic Survivors Detection: Among the 7 provided features, the most important ones for detecting Titanic survivors are gender, age, and the number of companions. Other features such as the embarkation port might not be as crucial for survivor detection. In designing the decision tree, we aim to utilize all 7 features. Ultimately, we conclude that having too many features and the presence of some less impactful features can lead to overfitting and a decrease in the accuracy of the decision tree.

Data Preprocessing: In this section, we convert categorical data into numerical data. For instance, we represent the 3 embarkation ports, S, Q, and C, as 0, 1, and 2 respectively. Additionally, for missing data in a feature (NaN), we use the median value of that feature.

Decision Tree Design Algorithm: To transform features from continuous and discrete states to binary states, we attempt to select a threshold among all data points of each feature that results in the minimum entropy. Data points smaller than the threshold are assigned 0, and those greater are assigned 1. Then, similar to the first section of the exercise, at each node of the tree, we try to choose a feature that leads to the least entropy, meaning the most reduction in ambiguity regarding the data label. Finally, we connect the determined nodes in each class and perform classification using the specified thresholds. In the overall algorithm, we consider the maximum number of tree layers as one of the stopping conditions, reaching the tree's leaf nodes. To this end, we calculate accuracy and the confusion matrix for different values of the number of tree layers.

The accompanying figure illustrates accuracy and the confusion matrix for various numbers of tree layers. As observed, when considering a low number of layers, since fewer features are utilized in classification, accuracy is compromised. On the other hand, if the number of layers becomes excessively high, the classifier loses its resistance against overfitting, resulting in decreased accuracy on test data.

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/dcd88cfd-b8d0-4d1a-ac49-d47939e6be07)

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/9d2ea918-c3bf-47e6-b598-fa8093786d45)

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/134f8db7-b27a-48d7-9254-0113bd2e72d0)

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/579f2a44-fd2a-4f25-9e0f-db41017c6cc7)

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/ddf5af5d-92b3-4bae-bbc7-9fd05819dab7)

**Part B:** Enhancing the Decision Tree Algorithm

As mentioned in the first section, one of the factors that can prevent overfitting of the decision tree is the removal of certain features. By eliminating features with higher entropy, we can increase the accuracy of the decision tree.

Another suitable approach to enhance the accuracy of the decision tree is the design of a random forest. In the random forest algorithm, when training a tree, we use a random set of training data points. In this manner, we design a number of trees (for example, 10 trees). Then, for classification, we gather the majority vote among the output labels of each tree in the forest and determine the final label. In part C, we implement this algorithm.

**Part C:** Using Random Forest
In accordance with the algorithm described in section B, we define a random forest with 10 trees. The following image depicts the confusion matrix along with the accuracy of the random forest.

![image](https://github.com/ErfanPanahi/Decision-Tree/assets/107314081/476ce773-c475-4904-9b23-a36f4005516b)

