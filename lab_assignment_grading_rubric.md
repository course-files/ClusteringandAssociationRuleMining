# Grading Rubric: Labs on Regression and Classification

The lab work is designed to be completed in groups of 4–5 students, with each
group submitting a single notebook. Each student is responsible for
understanding and being able to explain the work in their own group's notebook,
as well as contributing to the work itself.

This rubric has three parts, scored separately and combined at the end. This
is intended to distinguish between each member's contribution and understanding
of the work, while still rewarding the group for producing a polished, complete
notebook. It is also meant to discourage over-reliance on AI-generated solutions
that may reduce deep learning and understanding of the material.

| Part                            | What it measures                                            | Who is scored              | Weight in final grade                                   |
|---------------------------------|-------------------------------------------------------------|----------------------------|---------------------------------------------------------|
| A. Group Notebook               | Technical correctness and completeness of the submitted lab | The group, as one artifact | 55%                                                     |
| B. Individual Accountability    | Whether *each student* understands *their own* group's work | Each student individually  | 45%                                                     |
| C. Peer Contribution Adjustment | Whether effort was distributed amongst the group members.   | Each student individually  | Multiplier applied to each student's combined A+B score |

**Final individual grade** = `([0.55 × Group Notebook Score] + [0.45 × Individual Accountability Score]) × Peer Contribution Multiplier`

**Grading levels (we will use the Kenyan CBC Grading Levels 🙂)**:

| Level                             | Description               | Meaning                                                                                      |
|-----------------------------------|---------------------------|----------------------------------------------------------------------------------------------|
| **Exceeding Expectations (EE)**   | Above average performance | You consistently demonstrate exceptional understanding                                       |
| **Meeting Expectations (ME)**     | Expected performance      | You demonstrate adequate understanding                                                       |
| **Approaching Expectations (AE)** | Below expected level      | You are making progress but you need to make use of the lecturer's office hours for support. |
| **Below Expectations (BE)**       | Significantly below       | You require significant intervention, otherwise you will fail the course.                    |

---

## Part A: Group Notebook (100 points)

| #  | Criterion                                  | Weight | Exceeding Expectations (EE) (full marks)                                                                                                                                                                                                                                                                                                                                                                                           | Meeting Expectations (ME) (75%)                                                                                                                                                           | Approaching Expectations (AE) (50%)                                                                                                                                   | Below Expectations (BE) (0–25%)                                                                                                                                                        |
|----|--------------------------------------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | **Data Loading & EDA**                     | 8      | Shape, data types, and target correctly confirmed; distribution and relationship measures computed and *interpreted in prose*, not just printed; visualizations are labeled and each is followed by at least one sentence of insight.                                                                                                                                                                                              | Measures and visuals present and mostly correct; interpretation is too brief or generic.                                                                                                  | EDA is present but mostly descriptive output with no interpretation.                                                                                                  | EDA missing, copy-pasted without adaptation to this dataset, or materially incorrect.                                                                                                  |
| 2  | **Split Discipline to avoid Data Leakage** | 8      | Split performed correctly *before* feature selection/preprocessing, with a stated reason for the split ratio and (for classification) stratification correctly justified given class balance.                                                                                                                                                                                                                                      | Split is correctly sequenced and stratified but justification is missing or too brief.                                                                                                    | Split is present but incorrectly sequenced relative to the feature selection and data preprocessing/transformation, or stratification is omitted where it was needed. | No train/test split, or evidence of preprocessing/feature selection fit on the full dataset before splitting (data leakage is obvious).                                                |
| 3  | **Feature Selection**                      | 8      | At least two independent methods applied correctly on training data only, with a stated, dataset-specific decision (what was dropped/kept and why) — not merely output tables.                                                                                                                                                                                                                                                     | Methods applied on training data only, decision stated but weakly justified.                                                                                                              | Feature selection methods run, but on the full dataset (leakage) or with no resulting decision.                                                                       | Feature selection absent or copied without any adaptation to the specific dataset's actual correlated/near-duplicate features.                                                         |
| 4  | **Preprocessing Pipeline**                 | 14     | Encoding, imputation, and scaling correctly built as a `ColumnTransformer`/`Pipeline`, fit on training data only; *structural* vs. *random* missingness are handled differently and this distinction is explained; skew-correcting transform chosen correctly for the target's actual sign/range. *(For classification: resampling is included and correctly scoped to the training fold only, using an imbalance-safe pipeline.)* | Pipeline is correct and leakage-safe; missingness types are handled but not explicitly distinguished, e.g., missing at random and structural missingness; transform choice is reasonable. | Pipeline exists but has a leakage error (e.g., `fit_transform` used on test data), or missingness/imbalance handling is generic rather than dataset-appropriate.      | No pipeline (manual, ad hoc transforms), or the transform applied does not match the target's actual properties (e.g., Box-Cox attempted on a target containing zero/negative values). |
| 5  | **Modeling & Cross-Validation**            | 12     | At least five models compared using correctly configured k-fold (or stratified k-fold) cross-validation within a single pipeline structure; results presented as a table or chart, not scattered print statements.                                                                                                                                                                                                                 | Five-plus models compared, CV correctly configured, presentation is functional but unpolished.                                                                                            | Fewer than five models, or CV present but not stratified for an imbalanced classification target.                                                                     | No proper cross-validation (e.g., single train/test evaluation only), or models compared on inconsistent preprocessing.                                                                |
| 6  | **Diagnostics**                            | 10     | *(Regression)* Residual plot, Q-Q plot, and at least one formal test (Breusch-Pagan, Durbin-Watson, or Cook's distance) computed and interpreted against this dataset's actual output. *(Classification)* Confusion matrix, ROC, and precision-recall curve computed and interpreted, with explicit discussion of the minority class.                                                                                              | Diagnostics computed correctly; interpretation present but too vague rather than tied to specific values observed.                                                                        | Diagnostics computed but not interpreted at all, or only one diagnostic present.                                                                                      | Diagnostics missing, or the wrong diagnostic family used (e.g., regression diagnostics applied to a classification target).                                                            |
| 7  | **Evaluation of Multiple Models**          | 10     | Correct metrics for the task reported for every candidate model on the *held-out test set only*; for classification, macro/weighted distinction is explicitly discussed in relation to this dataset's class balance; the group states which model they selected and why.                                                                                                                                                           | Correct metrics reported; model selection stated but justification is too shallow.                                                                                                        | Metrics reported but computed on training data, or accuracy reported alone for an imbalanced classification target with no macro/weighted discussion.                 | Metrics missing, incorrect for the task, or no model selection made.                                                                                                                   |
| 8  | **Hyperparameter Tuning**                  | 8      | `GridSearchCV`/`RandomizedSearchCV` correctly applied to the selected model using the same CV scheme as was applied during the model training done after the data preprocessing stage; tuned performance compared explicitly against the untuned baseline.                                                                                                                                                                         | Tuning correctly applied; comparison against baseline is present but not discussed.                                                                                                       | Tuning applied but with an inconsistent CV scheme, or without a clear before/after comparison.                                                                        | No tuning attempted, or tuning applied in a way that leaks test data (e.g., `GridSearchCV.fit()` called on the full dataset).                                                          |
| 9  | **Explainability**                         | 12     | At least two distinct techniques applied (e.g., SHAP + coefficients/feature importance) and interpreted in terms of *the dataset's context* — which features drive predictions and why that makes domain sense.                                                                                                                                                                                                                    | Two techniques applied; interpretation present but generic or disconnected from the dataset's actual context.                                                                             | Only one technique applied, or output generated without any interpretation.                                                                                           | No explainability attempted, or output copied without adaptation (e.g., SHAP plot referencing feature names that do not exist in the dataset).                                         |
| 10 | **Model Persistence**                      | 5      | Full pipeline saved and reloaded, with a working prediction demonstrated on a new, manual input relevant to the dataset's context. *(Classification, if resampling used)* Explicit demonstration or statement that the resampler does not act at inference time.                                                                                                                                                                   | Pipeline saved/reloaded and predicts correctly; new input is present but minimal.                                                                                                         | Pipeline saved but not demonstrated with a new prediction, or reload step is missing.                                                                                 | Model persistence absent, or only the raw estimator (not the full pipeline) is saved.                                                                                                  |
| 11 | **Code Quality & Narrative**               | 5      | Code runs top-to-bottom without error; markdown cells narrate *decisions*, not just describe *outputs*; variable names and structure are legible to someone other than the authors.                                                                                                                                                                                                                                                | Code runs cleanly; narrative present but vague.                                                                                                                                           | Code runs with minor manual fixes needed; narrative is minimal or purely descriptive.                                                                                 | Code does not run end-to-end, or contains no narrative markdown at all.                                                                                                                |

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
|-------------------------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
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
  without dataset-specific adaptation is strongly discouraged.
