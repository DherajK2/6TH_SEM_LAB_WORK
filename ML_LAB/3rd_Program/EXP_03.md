
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

## Output

### Screenshot 1
<img src="https://raw.githubusercontent.com/DherajK2/6TH_SEM_LAB_WORK/main/ML_LAB/3rd_Program/EXP_03_ML_KNN_1.png" width="600"/>

---

### Screenshot 2
<img src="https://raw.githubusercontent.com/DherajK2/6TH_SEM_LAB_WORK/main/ML_LAB/3rd_Program/EXP_03_ML_KNN_2.png" width="600"/>
***

---

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

