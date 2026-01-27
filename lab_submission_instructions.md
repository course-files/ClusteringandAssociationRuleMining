# Lab Submission Instructions

---

## Student Details

**Name of the team on GitHub Classroom:**

**Team Member Contributions:**

**Member 1**

| **Details**                                                                                        | **Comment** |
|:---------------------------------------------------------------------------------------------------|:------------|
| **Student ID:**                                                                                    |             |
| **Name:**                                                                                          |             |
| **What part of the lab did you personally contribute to,** <br>**and what did you learn from it?** |             |

**Member 2**

| **Details**                                                                                        | **Comment** |
|:---------------------------------------------------------------------------------------------------|:------------|
| **Student ID:**                                                                                    |             |
| **Name:**                                                                                          |             |
| **What part of the lab did you personally contribute to,** <br>**and what did you learn from it?** |             |

**Member 3**

| **Details**                                                                                        | **Comment** |
|:---------------------------------------------------------------------------------------------------|:------------|
| **Student ID:**                                                                                    |             |
| **Name:**                                                                                          |             |
| **What part of the lab did you personally contribute to,** <br>**and what did you learn from it?** |             |

**Member 4**

| **Details**                                                                                        | **Comment** |
|:---------------------------------------------------------------------------------------------------|:------------|
| **Student ID:**                                                                                    |             |
| **Name:**                                                                                          |             |
| **What part of the lab did you personally contribute to,** <br>**and what did you learn from it?** |             |

**Member 5**

| **Details**                                                                                        | **Comment** |
|:---------------------------------------------------------------------------------------------------|:------------|
| **Student ID:**                                                                                    |             |
| **Name:**                                                                                          |             |
| **What part of the lab did you personally contribute to,** <br>**and what did you learn from it?** |             |

## Level of Difficulty and Video Demonstration

Submit the link to a short video (not more than 4 minutes) demonstrating your solution.

| **Key**                                       | **Value** |
|:----------------------------------------------|:----------|
| **Link to the video:**                        |           |
| **Level of Difficulty Chosen:**              |           |

## Scenario

Create new notebooks (**start from scratch**) and place them in the `lab_submission` folder for all parts of this assignment.

### Part 1: Clustering

1. Provide the code to download the `'./data/mall_customers_with_clusters.csv'` file, which contains the original dataset with an additional column for the cluster labels assigned by the K-Means algorithm. This code should work in Google Colab.
2. Provide the code to train a Support Vector Machine (SVM) model using the `X` and `y` variables, where `X` is the feature matrix and `y` is the target variable (the cluster labels). The SVM model should be trained to predict the cluster labels based on the features.
3. Provide the code to demonstrate the prediction of cluster labels using the trained SVM model. This should include a sample input and the predicted cluster label for that input.

---

## Part 2: Association Rule Mining

### Scenario

You are working as a data analyst for a retail store. Using the association rules derived from the dataset (`cleaned_rules`), you are required to provide business recommendations and design a simple recommender function.

### Part 2.1: Business Analysis (Critical Thinking)

- Examine the association rules in `cleaned_rules`.
- Present a business analysis report that addresses:
  - Which rules are useful and actionable for the business? (e.g., cross-promotions, store layout, bundling strategies).
  - Which rules are misleading or not useful despite appearing strong? (Consider support, confidence, and lift).
  - Recommend two specific business actions the company should implement based on your findings.

### Part 2.2: Recommender System (Programming)

**Baseline (Required)**

- Create a function called `dynamic_recommender_baseline(cart, rules_df)` that:
  - Accepts a list of products in the client’s cart as the antecedent.
  - Searches `cleaned_rules` for matching antecedents.
  - Returns the consequent(s) as the recommendations.

**Intermediate (Recommended)**

- Extend your function by creating another one named `dynamic_recommender_intermediate(cart, rules_df)` that is extended to:
  - Handle multiple items in the shopping cart.
  - If no rule matches, return "No recommendation available."
  - Rank recommendations using confidence (highest first).

**Advanced (Optional Challenge)**

- Enhance your recommender by creating another function named `dynamic_recommender_advanced(cart, rules_df)` that is extended to:
  - Allow the user to request top-N recommendations.
  - Incorporate lift to break ties between recommendations.
  - Compare your recommender’s output to a naïve baseline (e.g., always recommend top-selling products).
  - Briefly discuss: When would association rule recommenders fail in a businesses?

### Deliverables

1. Business Analysis Report.
2. Python implementation of the `dynamic_recommender` function. State whether you completed the Baseline, Intermediate, or Advanced version.
3. Sample runs of your function showing different shopping carts and outputs.

### Grading Approach

- Baseline = Pass (implementation works, basic analysis) >= 60%
- Intermediate = Merit (handles edge cases, thoughtful analysis) 75–85%
- Advanced = Distinction (robust function, strategic business insights) >= 86%

**Note 1:** The real challenge is not building the function—it is deciding which rules actually matter for the business. A good analyst filters the noise, questions misleading correlations, and translates data into profitable actions.

**Note 2:** The sophistication of the recommender is not measured by code complexity, but by how well it handles real-world edge cases—like sparse data, missing rules, and ambiguous ties.