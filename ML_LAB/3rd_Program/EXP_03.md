
# Machine Learning Lab – Experiment 3: K-Nearest Neighbour (KNN)


***

## Aim

For a given set of **randomly generated training data examples**, implement and demonstrate the **K-Nearest Neighbour (KNN)** algorithm to classify test data points based on their **k nearest neighbors** from the training data.

Develop a program to implement K-Nearest Neighbour algorithm to classify the randomly generated 100 values in the range ****. Perform the following based on dataset:
​

a. Label xi ∈ Class1 points (x1,…,x50) as follows: if (xi ≤ 0.5) then xi ∈ Class1, else xi ∈ Class2.
Book: Chapter - 2
b. Use KNN (k=1,2,3,4,5,20,30) on points x51,…,x100.
Book: Chapter - 2
Program no: 3 & 4

***

***

## Definition

The **K-Nearest Neighbour (KNN)** algorithm is a **supervised machine learning algorithm** used for **classification** and **regression** that classifies a new data point based on the **majority vote** of its **k most similar neighbors** from the training dataset.

***

## How the Algorithm Works

1. Store all training data points and their class labels.
2. For a new test data point, calculate the **distance** to all training points.
3. Sort distances in **ascending order** and select the **k nearest neighbors**.
4. Take **majority vote** among k neighbors to decide the class.
5. Assign the test point to the class with highest frequency.

***

## Algorithm: K-Nearest Neighbour (KNN)

**Input:** Training dataset, Test data point, Value of k
**Output:** Predicted class label for test point

1. Initialize k (number of nearest neighbors).
2. For each test point:
    - Calculate distance to all training points.
    - Sort distances in ascending order.
    - Pick first k distances (nearest neighbors).
    - Count frequency of each class among k neighbors.
    - Assign class with maximum count.
3. Output predicted class label.

***

***

# Source Code

## File 1 – create_dataset.py

This file creates a **CSV dataset** with random 1D points and their classes.

```python
import pandas as pd
import numpy as np

np.random.seed(42)

# Generate 50 training points
X_train = np.random.rand(50, 1)
y_train = ["Class1" if x[^1_0] <= 0.5 else "Class2" for x in X_train]

# Generate 20 test points
X_test = np.random.rand(20, 1) + 0.5  # Test points mostly > 0.5

# Training dataset
train_data = {
    "Feature_X": X_train.flatten(),
    "Class": y_train
}

# Test dataset (without labels)
test_data = {
    "Feature_X": X_test.flatten()
}

# Save training data
train_df = pd.DataFrame(train_data)
train_df.to_csv("knn_training_data.csv", index=False)

# Save test data
test_df = pd.DataFrame(test_data)
test_df.to_csv("knn_test_data.csv", index=False)

print("Training Dataset:")
print(train_df.head(10))
print("\nTest Dataset:")
print(test_df.head(10))
print("\nCSV files created successfully!")
```


## File 2 – knn_algorithm.py

This file reads CSV files and implements **KNN from scratch**.

```python
import pandas as pd
import numpy as np

# Read datasets
train_df = pd.read_csv("knn_training_data.csv")
test_df = pd.read_csv("knn_test_data.csv")

X_train = train_df[["Feature_X"]].values
y_train = train_df["Class"].values
X_test = test_df[["Feature_X"]].values

k = 3

def euclidean_distance(point1, point2):
    return np.sqrt(np.sum((point1 - point2)**2))

print("KNN Classification Results (k =", k, "):")
print("-" * 50)

for i in range(len(X_test)):
    test_point = X_test[i]
    distances = []
    
    # Calculate distance to all training points
    for j in range(len(X_train)):
        dist = euclidean_distance(test_point, X_train[j])
        distances.append((dist, y_train[j]))
    
    # Sort by distance
    distances.sort()
    
    # Get k nearest neighbors
    neighbors = distances[:k]
    neighbor_classes = [neighbor[^1_1] for neighbor in neighbors]
    
    # Majority vote
    prediction = max(set(neighbor_classes), key=neighbor_classes.count)
    
    print(f"Test Point {i+1}: X={test_point[^1_0]:.3f} -> Predicted: {prediction}")
    
print("\nKNN algorithm completed successfully!")
```


***

## Output

### Screenshot 1
<img src="https://raw.githubusercontent.com/DherajK2/6TH_SEM_LAB_WORK/main/ML_LAB/3rd_Program/EXP_03_ML_KNN_1.png" width="600"/>

---

### Screenshot 2
<img src="https://raw.githubusercontent.com/DherajK2/6TH_SEM_LAB_WORK/main/ML_LAB/3rd_Program/EXP_03_ML_KNN_2.png" width="600"/>
***

---

## Explanation

- Dataset contains **1D feature (Feature_X)** and **binary classes (Class1, Class2)**.
- **Training data**: 50 points used to find nearest neighbors.
- **Test data**: 20 new points classified using KNN.
- **Distance metric**: Euclidean distance between 1D points.
- **k=3**: Each test point classified based on 3 nearest training neighbors.
- **Majority voting**: Class with highest frequency among neighbors wins.
- Points closer to 0.5 boundary may get mixed predictions.

***

## Viva Questions

1. **What is the KNN Algorithm?**
Supervised learning algorithm that classifies based on k nearest neighbors using distance metric.
2. **What type of learning does KNN perform?**
Supervised learning (classification/regression).
3. **What does 'k' represent in KNN?**
Number of nearest neighbors to consider for classification.
4. **What distance metric is commonly used in KNN?**
Euclidean distance.
5. **What happens when k=1?**
Classifies based on single nearest neighbor (may overfit).
6. **What happens when k is very large?**
May underfit as decision depends on too many neighbors.
7. **Does KNN build a model during training?**
No, it's a lazy learner that stores all training data.
8. **What is the main advantage of KNN?**
Simple, intuitive, and works with any distance metric.
9. **What is the main limitation of KNN?**
Computationally expensive for large datasets.
10. **How does KNN handle classification?**
Majority voting among k nearest neighbors' classes.
<span style="display:none">[^1_10][^1_2][^1_3][^1_4][^1_5][^1_6][^1_7][^1_8][^1_9]</span>

<div align="center">⁂</div>

[^1_1]: https://www.appliedaicourse.com/blog/knn-algorithm-in-machine-learning/

[^1_2]: https://www.reddit.com/r/MLQuestions/comments/18a9f5f/how_does_the_knn_classifier_actually_work/

[^1_3]: https://roboticsbiz.com/pros-and-cons-of-the-k-nearest-neighbors-knn-algorithm/

[^1_4]: http://becbapatla.ac.in/wp-content/uploads/20ECL501-SOC3-MACHINE-LEARNING-LAB-MANUAL.pdf

[^1_5]: https://arize.com/blog-course/knn-algorithm-k-nearest-neighbor/

[^1_6]: https://app.myeducator.com/reader/web/1421a/11/q07a0/

[^1_7]: https://www.scribd.com/document/936051719/ML-Lab-Manual-Exp-1-to-10

[^1_8]: https://www.pinecone.io/learn/k-nearest-neighbor/

[^1_9]: https://www.tencentcloud.com/techpedia/101813

[^1_10]: https://www.scribd.com/document/949660493/Machine-Learning-Lab-Manual


---

# Machine Learning Lab – Experiment 3: K-Nearest Neighbour (KNN)


***

## Aim

Develop a program to implement **K-Nearest Neighbour algorithm** to classify the **randomly generated 100 values** in the range ****. Perform the following based on dataset:[^2_1]

**a.** Label **xi ∈ Class1 points (x1,…,x50)** as follows: **if (xi ≤ 0.5)** then **xi ∈ Class1**, **else xi ∈ Class2**.
**Book: Chapter - 2**
**b.** Use **KNN** (k=1,2,3,4,5,20,30) on **points x51,…,x100**.
**Book: Chapter - 2**
**Program no: 3 \& 4**

***

***

## Definition

The **K-Nearest Neighbour (KNN)** algorithm is a **supervised learning algorithm** that classifies data points based on the **majority class** of their **k closest neighbors** measured by distance metrics like Euclidean distance.

***

## How the Algorithm Works

1. Generate 100 random values in  range.[^2_1]
2. Label first 50 points: ≤0.5 → **Class 1**, >0.5 → **Class 2**.
3. Use first 50 points as training data.
4. For test points (51-100), find k nearest training neighbors.
5. Classify based on majority vote of k neighbors.

***

## Algorithm: K-Nearest Neighbour (KNN)

**Input:** Training data (x1..x50 with labels), Test data (x51..x100), k values
**Output:** Predicted classes for test points

1. Generate X = random(100) ∈.[^2_1]
2. y = Class labels for X[0:50] where xi≤0.5 → Class1 else Class2.
3. For each k in:[^2_2][^2_3][^2_4][^2_5][^2_1]
    - Train KNN with k neighbors on X[0:50], y.
    - Predict classes for X[50:100].
4. Display results and visualizations.

***

***

# Source Code

## File 1 – knn_part_a.py

This file implements **part (a)** - generates data and classifies with **k=3**.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.neighbors import KNeighborsClassifier
np.random.seed(42)


X =np.random.rand(100).reshape(-1,1)
y=np.array(["Class 1" if x<=0.5 else "Class 2" for x in X[:50]])


knn = KNeighborsClassifier(n_neighbors=3)


knn.fit(X[:50],y)


y_pred = knn.predict(X[:50])


final_labels = np .concatenate((y,y_pred))


plt.scatter(X[:50],[^2_1]*50, c='blue',label='Labelled Data(Class 1 & 2)')


plt.scatter(X[:50],[^2_2]*50,c='red',label='Predicted Data')


plt.xlabel("X values")
plt.ylabel("Class")
plt.legend()
plt.title("KNN Classification of Randomly Generated Points")
plt.show()


for i in range(100):
    print(f"x{i+1}:{X[i][^2_0]:.3f} -> {final_labels[i]}")
```


## File 2 – knn_part_b.py

This file implements **part (b)** - tests **k=1,2,3,4,5,20,30** values.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.neighbors import KNeighborsClassifier


np.random.seed(42)


X = np.random.rand(100).reshape(-1, 1)


# Fix 1
y = np.array(["Class 1" if x[^2_0] <= 0.5 else "Class 2" for x in X[:50]])


k_values = [1, 2, 3, 4, 5, 20, 30]
results = {}


for k in k_values:
    knn = KNeighborsClassifier(n_neighbors=k)
    
    # Fix 2
    knn.fit(X[:50], y)
    
    y_pred = knn.predict(X[:50])
    results[k] = y_pred


plt.figure(figsize=(10, 6))
colors = ['red', 'blue', 'green', 'orange', 'purple', 'brown', 'pink']


for i, k in enumerate(k_values):
    # Fix 3
    plt.scatter(X[:50], [i]*50, c=[colors[i]]*50, label=f'k={k}')


plt.xlabel("X Values")
plt.ylabel("Different k-values")
plt.legend()
plt.title("KNN classification for different k-values")
plt.show()


# Fix 4 + 5
for k in k_values:
    print(f"\nClassification result for k={k}:")
    for i in range(50):
        print(f"X{i+1}: {X[i][^2_0]:.3f} -> {results[k][i]}")
```


***

## Output

### Output of File 1 – knn_part_a.py

```
x1:0.375 -> Class 1
x2:0.950 -> Class 2
x3:0.732 -> Class 2
...
[Scatter plot showing labelled vs predicted data]
```


### Output of File 2 – knn_part_b.py

```
Classification result for k=1:
X1: 0.375 -> Class 1
X2: 0.950 -> Class 2
...

Classification result for k=2:
X1: 0.375 -> Class 1
...

[Scatter plot showing classification for different k values]
```


***

## Explanation

- **100 random values** generated in range **** using `np.random.rand(100)`.[^2_1]
- **First 50 points (x1..x50)** labelled: **xi ≤ 0.5 → Class 1**, else **Class 2**.
- **File 1**: Uses **k=3** to demonstrate basic KNN classification with visualization.
- **File 2**: Tests **k=** showing how different k values affect boundaries.[^2_3][^2_4][^2_5][^2_2][^2_1]
- **Training**: Uses first 50 points with known labels.
- **Visualization**: Shows data distribution and classification patterns for different k.

***

## Viva Questions

1. **What is KNN Algorithm?**
Classifies data points based on majority vote of k nearest neighbors.
2. **How are classes assigned in part (a)?**
xi ≤ 0.5 → Class 1, else Class 2 for first 50 points.
3. **What range are the 100 values generated from?**
using uniform random distribution.[^2_1]
4. **Why test different k values?**
To observe effect on classification boundary and overfitting/underfitting.
5. **What distance metric does sklearn KNN use by default?**
Euclidean distance.
6. **What happens when k=1 vs k=30?**
k=1 may overfit (noisy), k=30 smooths boundary (may underfit).
7. **Is KNN a lazy learner?**
Yes, no explicit training phase - stores all data.
8. **Main advantage of KNN?**
Simple, non-parametric, works for multi-class problems.
9. **Main disadvantage of KNN?**
Slow prediction for large datasets (O(n) computation).
10. **How many training points are used?**
First 50 points (x1 to x50) with known labels.
<span style="display:none">[^2_6]</span>

<div align="center">⁂</div>

[^2_1]: https://www.appliedaicourse.com/blog/knn-algorithm-in-machine-learning/

[^2_2]: https://www.reddit.com/r/MLQuestions/comments/18a9f5f/how_does_the_knn_classifier_actually_work/

[^2_3]: https://roboticsbiz.com/pros-and-cons-of-the-k-nearest-neighbors-knn-algorithm/

[^2_4]: http://becbapatla.ac.in/wp-content/uploads/20ECL501-SOC3-MACHINE-LEARNING-LAB-MANUAL.pdf

[^2_5]: https://arize.com/blog-course/knn-algorithm-k-nearest-neighbor/

[^2_6]: image.jpg

