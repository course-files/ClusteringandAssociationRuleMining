# Lab Assignment for Clustering and Association Rule Mining

Your group has been assigned one of the datasets below. Work through the complete
modeling pipeline we went through during the lab: from installation of
dependencies all the way to model persistence, applied to your assigned dataset.
Submit one Jupyter notebook (`.ipynb`) per group.

**This must be your own analysis of your assigned dataset, not the demonstration
notebook with different column names, i.e. you have to customize your analysis.**
Each dataset has its own missingness patterns, correlated features, and target
shape. Your decisions should reflect that. Refer to
[the rubric](./lab_assignment_grading_rubric.md) for what each
stage needs to earn full marks.

## Assigned Synthetic Datasets for Clustering

| Dataset                                                                               | Context                                                             | Unit of analysis       | Group                       |
|---------------------------------------------------------------------------------------| ------------------------------------------------------------------- | ---------------------- |-----------------------------|
| [`ecommerce_customer_behavior.csv`](./data/ecommerce_customer_behavior.csv)           | Online retail RFM-style behavior (recency, frequency, order value)  | Customers              | C                           |
| [`bank_wealth_management.csv`](./data/bank_wealth_management.csv)                     | Retail banking segmentation (balance, transaction activity, tenure) | Bank accounts          | B                           |
| [`hr_workforce_segmentation.csv`](./data/hr_workforce_segmentation.csv)               | Workforce planning (experience, salary, training, reports)          | Employees              | *Not assigned to any group* |
| [`retail_store_performance.csv`](./data/retail_store_performance.csv)                 | Store performance (revenue, foot traffic, staffing, size)           | **Stores**, not people | A                           |
| [`agricultural_cooperative_farmers.csv`](./data/agricultural_cooperative_farmers.csv) | Farmer segmentation for a cooperative (farm size, yield, income)    | Farmers                | D                           |

**Beyond the notebook**, every group member should individually complete:
- A 2-3-minute one-on-one conversation (defense) where you will be asked
  **only one** random question related to a decision that was made in your
  group's notebook. Note that this is not necessarily only the part you
  personally coded; you are expected to understand the entire group submission
  (the whole notebook).
- A **private** peer-contribution rating of your teammates. This will adjust
  each teammate's final grade according to their group contribution.

**Logistics**:
- Groups of 5, as assigned from Business Intelligence 1.
- Use the dataset that has been assigned to your group. Do not substitute it
  with a different dataset.
