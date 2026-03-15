# Machine Learning Lab – Experiment 2: Find-S Algorithm

---

## Aim

For a given set of training data examples stored in a **CSV file**, implement and demonstrate the **:contentReference[oaicite:0]{index=0}** to output a description of the set of all hypotheses consistent with the training examples in **:contentReference[oaicite:1]{index=1}**.

---

***

## Definition

The **Find-S Algorithm** is a concept learning algorithm that finds the **most specific hypothesis** that fits all the **positive training examples** in a dataset.

It starts with the **most specific hypothesis** and gradually **generalizes it** whenever it encounters differences between positive training examples.

---

## How the Algorithm Works

1. Initialize the hypothesis **h** to the most specific hypothesis.
2. Consider the first **positive training example**.
3. For each attribute in the example:
   - If the hypothesis value is different from the example value, replace it with **?**.
4. Ignore all **negative training examples**.
5. Continue until all training examples are processed.
6. The resulting hypothesis is the **most specific hypothesis** consistent with the positive examples.

---

## Algorithm: Find-S

**Input:** Positive instances in the Training dataset  
**Output:** Hypothesis `h`

1. Initialize 'h' to the most specific hypothesis.  
   h = <Φ, Φ, ..., Φ>

2. Generalize the initial hypothesis for the first positive instance  
   (Since 'h' is more specific.)

3. For each subsequent instance:  
   - If it is a positive instance:  
     - Check for each attribute value in the instance with the hypothesis 'h'.  
     - If the attribute value is the same as the hypothesis value, then do nothing.  
     - Else if the attribute value is different than the hypothesis value, change it to '?' in 'h'.  
   - Else if it is a negative instance:  
     - Ignore it.

---

***

# Source Code

## File 1 – create_dataset.py

This file creates a dataset and stores it in a **CSV file**.

```python
import pandas as pd

# dataset
data = {
    "Citation": ["Good", "Good", "Poor", "Good"],
    "Size": ["Large", "Large", "Large", "Small"],
    "InLibrary": ["Yes", "Yes", "Yes", "Yes"],
    "Price": ["Expensive", "Cheap", "Cheap", "Cheap"],
    "Edition": ["Latest", "Latest", "Old", "Latest"],
    "Buy": ["Yes", "Yes", "No", "Yes"]
}

# convert to dataframe
df = pd.DataFrame(data)

# display dataset
print("Dataset:\n")
print(df)

# save to csv
df.to_csv("training_data.csv", index=False)

print("\nCSV file created successfully")
```




## File 2 – finds_algorithm.py

This file reads the CSV file and applies the **Find-S Algorithm**.
```python
import pandas as pd

# read dataset
df = pd.read_csv("training_data.csv")

# separate attributes and target
X = df.iloc[:, :-1]
y = df.iloc[:, -1]

# initialize hypothesis
hypothesis = None

for i in range(len(X)):

    if y[i] == "Yes":

        if hypothesis is None:
            hypothesis = list(X.iloc[i])
        else:
            for j in range(len(hypothesis)):
                if hypothesis[j] != X.iloc[i, j]:
                    hypothesis[j] = '?'

print("Final Hypothesis:")
print(hypothesis)
```
---

## Output

### Output of File 2 – finds_algorithm.py

Final Hypothesis:  
['Good', '?', 'Yes', '?', 'Latest']

---

## Explanation

- The dataset contains attributes **Citation, Size, InLibrary, Price, Edition** and the target attribute **Buy**.
- The **Find-S Algorithm** considers only **positive examples** (Buy = Yes).
- The first positive example becomes the **initial hypothesis**.
- When differences occur between attributes of positive examples, they are replaced with **?**, meaning any value is acceptable.
- The final result is the **most specific hypothesis** that satisfies all positive training examples.

---

## Viva Questions

1. **What is the Find-S Algorithm?**  
   Determines the most specific hypothesis consistent with all positive training examples.

2. **What type of learning does Find-S perform?**  
   Concept learning.

3. **Does Find-S consider negative examples?**  
   No. It ignores negative examples.

4. **What does the symbol '?' represent?**  
   Any value is acceptable for that attribute.

5. **What is the main limitation of Find-S?**  
   Ignores negative examples and cannot handle inconsistent training data.

6. **What type of hypothesis does Find-S produce?**  
   The most specific hypothesis covering all positive examples.

7. **In which field is Find-S used?**  
   Machine Learning for concept learning problems.

8. **What is the input to Find-S?**  
   A set of training examples with attributes and a target.

9. **What is the output of Find-S?**  
   The most specific hypothesis consistent with positive examples.

10. **What is a hypothesis in machine learning?**  
    A possible rule or function mapping inputs to outputs.
