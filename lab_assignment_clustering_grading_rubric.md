# Grading Rubric: Lab on K-Means Clustering

The lab work is designed to be completed in groups of 4–5 students, with each
group submitting a single notebook. Each student is responsible for
understanding and being able to explain the work in their own group's notebook,
as well as contributing to the work itself.

This rubric has three parts, scored separately and combined at the end. This
is intended to distinguish between each member's contribution and understanding
of the work, while still rewarding the group for producing a polished, complete
notebook. It is also meant to discourage over-reliance on AI-generated solutions
that may reduce deep learning and understanding of the material.

Clustering is unsupervised: there is no target variable, no train/test split in
the supervised sense, no class imbalance, and no resampling. Several criteria
below are therefore restructured from their supervised-learning equivalents
rather than simply relabeled — most notably, "choosing the number of clusters"
replaces both model comparison and hyperparameter tuning as the central
methodological decision in this lab, since it is the one choice with no ground
truth to check it against.

| Part                            | What it measures                                            | Who is scored              | Weight in final grade                                   |
|----------------------------------|---------------------------------------------------------------|-----------------------------|-----------------------------------------------------------|
| A. Group Notebook               | Technical correctness and completeness of the submitted lab | The group, as one artifact | 55%                                                     |
| B. Individual Accountability    | Whether *each student* understands *their own* group's work | Each student individually  | 45%                                                     |
| C. Peer Contribution Adjustment | Whether effort was distributed amongst the group members.   | Each student individually  | Multiplier applied to each student's combined A+B score |

**Final individual grade** = `([0.55 × Group Notebook Score] + [0.45 × Individual Accountability Score]) × Peer Contribution Multiplier`

**Grading levels (we will use the Kenyan CBC Grading Levels 🙂)**:

| Level                             | Description               | Meaning                                                                                      |
|-----------------------------------|---------------------------|------------------------------------------------------------------------------------------------|
| **Exceeding Expectations (EE)**   | Above average performance | You consistently demonstrate exceptional understanding                                       |
| **Meeting Expectations (ME)**     | Expected performance      | You demonstrate adequate understanding                                                       |
| **Approaching Expectations (AE)** | Below expected level      | You are making progress but you need to make use of the lecturer's office hours for support. |
| **Below Expectations (BE)**       | Significantly below       | You require significant intervention, otherwise you will fail the course.                    |

---

## Part A: Group Notebook (100 points)

| #  | Criterion                                          | Weight | Exceeding Expectations (EE) (full marks)                                                                                                                                                                                                                                                                                | Meeting Expectations (ME) (75%)                                                                                                                          | Approaching Expectations (AE) (50%)                                                                                                                            | Below Expectations (BE) (0–25%)                                                                                                                                        |
|----|-----------------------------------------------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **Data Loading & EDA**                             | 8      | Shape and data types correctly confirmed; identifier columns (e.g. a customer or account ID) are explicitly recognized and excluded from every subsequent statistic and plot; distribution and relationship measures are computed and *interpreted in prose*, not just printed; each visualization is followed by at least one sentence of insight. | Measures and visuals present and mostly correct; identifier columns are excluded from clustering but may still leak into an early EDA statistic or plot; interpretation is too brief or generic. | EDA is present but mostly descriptive output with no interpretation, or an identifier column is left in a distribution/correlation summary without comment.       | EDA missing, copy-pasted without adaptation to this dataset, or materially incorrect.                                                                                  |
| 2  | **Feature Inclusion/Exclusion Justification**      | 8      | Clearly and correctly states, with dataset-specific reasoning, which numeric features are used in the distance calculation, which identifier(s) are dropped entirely, and which categorical variable(s) are deliberately set aside for *post-hoc profiling* rather than encoded into the clustering itself.            | States the same decisions correctly but justification is generic ("we removed the ID column") rather than tied to why a categorical variable specifically was reserved for profiling. | A feature-inclusion decision is made but not explained, or a categorical variable is one-hot encoded into the clustering with no discussion of that choice's effect on distance. | No stated feature selection reasoning; identifier or categorical columns feed directly into the clustering algorithm with no apparent awareness of the consequence.  |
| 3  | **Redundant/Correlated Feature Check**             | 8      | Correlation among the numeric features intended for clustering is explicitly checked (e.g., a correlation matrix or heatmap) *before* clustering, with a stated conclusion about whether any feature pair risks double-counting the same signal in the distance calculation.                                          | Correlation is checked and shown but the group does not explicitly connect the result to a decision about the features used for clustering.               | Correlation is computed as a routine EDA step but never revisited in the context of feature selection for clustering.                                             | No correlation check performed among the clustering features at all.                                                                                                  |
| 4  | **Preprocessing Pipeline (Scaling & Missing Data)** | 14     | Standardization (or another justified scaling method) is applied and its necessity explicitly justified given the features' differing units/ranges; *structural* vs. *random* missingness are handled differently in the data with this distinction explained; the resulting scaled data is confirmed (e.g., mean ≈ 0, SD ≈ 1). | Scaling and missingness handling are both correct, but the structural-vs-random distinction is not explicitly named even if handled sensibly.             | Scaling is applied, but generically, with no missingness-type distinction, or missing data is dropped without justification.                                       | No scaling applied before clustering (a critical, not cosmetic, omission for K-Means), or scaling is fit and confirmed incorrectly.                                    |
| 5  | **Determining the Optimal Number of Clusters (k)** | 12     | At least three distinct validity approaches are used (e.g., elbow/inertia plus silhouette plus one of Davies-Bouldin or Calinski-Harabasz) across a reasonable range of k; the group explicitly checks whether the methods agree, and states its reasoning when they do not.                                          | At least two validity approaches are used and compared; agreement/disagreement between them is noted but not discussed in depth.                          | Only the elbow method is used, with no corroborating metric, or metrics are computed but never compared to each other.                                             | No systematic method for choosing k; k is picked arbitrarily or copied from another dataset's value with no justification for this dataset.                            |
| 6  | **Cluster Diagnostics**                            | 10     | Final cluster sizes are checked for balance (no degenerate near-empty cluster passes unnoticed), and the chosen solution's silhouette score (or equivalent) is reported and interpreted in light of the comparison in Criterion 5, not just restated as a number.                                                     | Cluster sizes and a validity score are both reported, but interpretation is thin ("the silhouette score is 0.42") without connecting it back to what that means for this solution. | Only one of the two checks (balance or validity score) is performed.                                                                                                | No post-fit diagnostic check performed on the final clustering solution at all.                                                                                        |
| 7  | **Justification of the Final Chosen k**            | 10     | The group explicitly compares at least two candidate values of k side by side (e.g., in a table), states which was chosen and why, and — if the statistically best-scoring k was *not* chosen — gives an explicit, defensible business or interpretability reason for the alternative choice.                        | A final k is chosen and stated correctly, but the comparison against the next-best candidate is shallow or the reasoning for the choice is asserted rather than argued. | A k is chosen with reference to the Criterion 5 output, but no real comparison against alternative candidate values is shown.                                       | The chosen k is not connected to any of the evidence gathered in Criterion 5; the number appears to have been picked independently of the analysis shown.               |
| 8  | **Robustness / Sensitivity Check**                 | 8      | The group tests whether their clustering solution is stable under at least one reasonable variation — e.g., a different random seed or `n_init`, an alternative scaling method (standardization vs. normalization), or a brief comparison against one alternative clustering algorithm — and reports whether the conclusion changes. | One robustness variation is attempted, but the comparison is superficial (run once, result shown, no comment on whether it matters).                        | A robustness check is mentioned in narrative but not actually demonstrated in code.                                                                                 | No robustness or sensitivity check attempted; the single fitted solution is treated as if it were the only possible outcome.                                           |
| 9  | **Cluster Profiling & Explainability**             | 12     | Clusters are profiled using at least two techniques (e.g., group-wise means/standard deviations of the clustering features, plus either a categorical cross-tabulation or a surrogate decision tree), with each named cluster's profile interpreted in genuine business terms specific to this dataset.               | Profiling is performed correctly with at least one technique, and interpretation is present but generic (e.g., cluster labels are not clearly tied back to the actual computed profile values). | Cluster profile statistics are computed and printed but never translated into a named, interpreted segment.                                                        | No cluster profiling performed, or interpretation is copied from an unrelated dataset's segment narrative without adaptation to this dataset's actual output.          |
| 10 | **Model Persistence**                              | 5      | The fitted scaler and fitted clustering model are saved *together* (not the model alone) and reloaded to demonstrate assignment of a new, manually constructed data point to an existing cluster, with a brief note on why the scaler must travel with the model.                                                    | Scaler and model are both saved and reloaded correctly; the new-point demonstration is present but minimal.                                               | Only the model is saved, or the reload step is shown without an actual new-point prediction demonstrated.                                                            | No persistence attempted, or persistence is attempted but does not actually reproduce a working prediction on reload.                                                  |
| 11 | **Code Quality & Narrative**                       | 5      | Code runs top-to-bottom without error; markdown cells narrate *decisions* (why this scaling method, why this k), not just describe *outputs*; variable names and structure are legible to someone other than the authors.                                                                                             | Code runs cleanly; narrative present but vague.                                                                                                            | Code runs with minor manual fixes needed; narrative is minimal or purely descriptive.                                                                              | Code does not run end-to-end, or contains no narrative markdown at all.                                                                                                |

**Total: 100 points**

---

## Part B: Individual Accountability (100 points)

This will be scored per student, using **the student's own group's notebook and
dataset** as the reference point. No student receives this score by proxy from
a teammate's performance.

It involves a 2-3-minute one-on-one conversation per student where you will be
asked **only one** random question related to a decision that was made in your
group's notebook.

| Level                         | Points | Description                                                                                                                                                                                             |
|-------------------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exceeding Expectations (EE)   | 70–100 | Explains the reasoning behind a specific decision in their own notebook accurately and fluently; can answer a natural follow-up ("what would happen if you had skipped that step?") without hesitation. |
| Meeting Expectations (ME)     | 60–69  | Correctly describes *what* the notebook does at the question's point, but reasoning for *why* is partial or requires prompting.                                                                         |
| Approaching Expectations (AE) | 50–59  | Can locate the relevant cell but cannot explain the underlying decision; answer suggests limited familiarity with that section.                                                                         |
| Below Expectations (BE)       | 0–49   | Cannot explain the code at all, or the explanation contradicts what the notebook actually does — suggesting the student did not produce or understand this part of the work.                            |

**Total: 100 points**

---

## Part C: Peer Contribution Adjustment

Each student privately rates every teammate (not themselves) on a simple
contribution scale immediately after submission, before any grades are released.
The average peer rating per student is converted into a multiplier applied to
the specific student's own (A+B) combined score.

| Average peer rating                                          | Multiplier |
|--------------------------------------------------------------|------------|
| Consistently rated as a strong, reliable contributor (5)     | 1.05       |
| Rated as an expected, adequate contributor (4)               | 1.00       |
| Rated as a below-expectation contributor by most peers (2-3) | 0.90       |
| Rated as a non-contributor by a majority of peers (1)        | 0.75       |

If peer ratings for a student are sharply inconsistent (e.g., some rate them
highly, others rate them as a non-contributor), do not average blindly — this
is a signal to follow up with the group directly before finalizing that
student's multiplier, rather than a mechanical case.

---

**Notes:**
- **A submission using the provided dataset verbatim, with no visible
  adaptation of feature names, business framing, or decisions to that dataset's
  actual properties, will be treated as a Part A ceiling of "Approaching
  Expectations (AE)" regardless of how complete it looks**. Completeness
  without dataset-specific adaptation is strongly discouraged. For this lab
  specifically, this includes cluster interpretation narratives that read as
  though they were written for a different dataset's segments (e.g., customer
  language applied to a dataset where the unit of analysis is stores or farms).
- **Criteria 5 through 7 carry more combined weight (30 of 100 points) than any
  other stage of this rubric.** This is deliberate: in supervised learning, a
  wrong modeling choice is eventually caught by a held-out metric; in
  clustering, there is no such check, so the quality of the *reasoning* behind
  the chosen k is the primary evidence markers have that the group understood
  what they were doing, rather than accepting whichever k the elbow plot
  visually suggested first.
