# Instructor Effectiveness Modeling (EdTech)

**Data Science / AI Content Specialist Intern Assignment**

A complete end-to-end machine learning pipeline that defines, measures, and predicts instructor effectiveness using learner outcomes, engagement, and feedback data from an EdTech platform.

---

## 📌 Project Overview

EdTech platforms often run the same course across multiple batches taught by different instructors. Understanding **which instructors are truly effective** is critical for quality control, instructor development, and learner success.

This project tackles the problem by:

1. Defining a transparent **Instructor Effectiveness Score**
2. Converting the score into actionable tiers (**Low / Medium / High**)
3. Aggregating batch-level data to the instructor level
4. Building classical ML models to predict effectiveness tiers
5. Interpreting results and discussing real-world limitations & ethics

> **Note:** There is no single “correct” answer. The focus is on structured thinking, clear assumptions, and thoughtful interpretation rather than pure model accuracy.

---

## 🎯 Business Objective

Estimate instructor effectiveness using available data from:

- **Learner Outcomes** → completion rate, dropout rate, score improvement, quiz scores  
- **Engagement** → video watch time, assignment submission, forum activity  
- **Feedback** → average rating and response rate  

Then build a model that predicts effectiveness tiers to support decision-making in an EdTech product.

---

## 🗂️ Dataset

- **Rows**: 2,000 course batches  
- **Instructors**: 120 unique instructors  
- **Courses**: 25 unique courses  

Each row represents one batch taught by one instructor.

| Category              | Columns                                      |
|-----------------------|----------------------------------------------|
| Identifiers           | `batch_id`, `instructor_id`, `course_id`     |
| Learner Outcomes      | `completion_rate`, `dropout_rate`, `avg_score_improvement`, `avg_quiz_score` |
| Engagement            | `avg_watch_time`, `assignment_submission_rate`, `forum_activity_rate` |
| Feedback              | `avg_feedback_score`, `feedback_response_rate` |

---

## 🧠 Methodology

### 1. Exploratory Data Analysis
- Distributions, correlations, missing values, and anomalies
- Strong negative correlation between completion and dropout rates
- Batch count per instructor ranges from 7 to 31

### 2. Defining Instructor Effectiveness
A weighted composite score was designed:

| Component              | Weight | Rationale                                      |
|------------------------|--------|------------------------------------------------|
| Retention              | 30%    | Core business outcome (completion + retention) |
| Learning Gain          | 25%    | Actual knowledge/skill improvement             |
| Engagement             | 25%    | Active learner participation                   |
| Learner Feedback       | 20%    | Direct perception of teaching quality          |

The score is then converted into **Low / Medium / High** tiers using quantile thresholds.

### 3. Aggregation to Instructor Level
Batch-level metrics are aggregated using:
- Mean (typical performance)
- Standard deviation (consistency)
- Number of batches & distinct courses taught

### 4. Machine Learning Models
Classical models only (as per constraints):

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

**Primary evaluation metric**: Macro F1-score (treats all tiers equally)

### 5. Interpretation
- Feature importance (impurity-based + permutation)
- Confusion matrix and classification reports
- Discussion of confounding variables and real-world failure modes

---

## 🛠️ Tech Stack

- **Python 3**
- **pandas** & **numpy** – data manipulation
- **scikit-learn** – modeling & evaluation
- **matplotlib** & **seaborn** – visualization
- **Jupyter / Google Colab** – reproducible notebook

**Not used** (as per assignment rules): LLMs, external datasets, AutoML tools

---

## 🚀 How to Run

1. Clone the repository
2. Open `Instructor_Effectiveness_Modeling.ipynb` in Google Colab or Jupyter
3. Place the dataset CSV in the same directory
4. Run all cells top-to-bottom

```bash
# Optional: create a virtual environment
python -m venv venv
source venv/bin/activate   # or venv\Scripts\activate on Windows
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

---

## 📊 Key Insights

- Retention metrics (completion & dropout) are the strongest drivers of effectiveness.
- Learning gains and learner feedback also contribute meaningfully.
- Consistency across batches (low standard deviation) is an important signal.
- Engagement metrics are useful but secondary — necessary but not sufficient.
- The model should **not** be used as a sole high-stakes performance evaluation tool due to missing context (course difficulty, cohort quality, etc.).

---

## ⚠️ Limitations & Ethical Considerations

- The effectiveness score is a **constructed** target — it embeds subjective weighting choices.
- No control for course difficulty or learner prior ability → potential confounding.
- Feedback is self-selected and may be biased.
- High-stakes use risks unfair treatment of instructors teaching harder courses or newer cohorts.
- Recommended use: diagnostic tool + human oversight, not automated evaluation.

---

## 📁 Repository Structure

```
├── Instructor_Effectiveness_Modeling.ipynb   # Main notebook
├── instructor_effectiveness_dataset_....csv  # Dataset
└── README.md                                 # Project documentation
```

---

## 📝 Assignment Constraints Followed

- ✅ Only allowed libraries used  
- ✅ No external datasets or LLMs  
- ✅ Clear reasoning and justified assumptions  
- ✅ Reproducible notebook with markdown explanations  
- ✅ Answers to all mandatory analysis questions  

---

## 👤 Author

Data Science / AI Content Specialist Intern Assignment  
Submitted as part of the evaluation process.

---

**Focus of evaluation**: Understanding of the problem • Feature engineering quality • ML fundamentals • Interpretation & communication • Awareness of limitations and ethics

