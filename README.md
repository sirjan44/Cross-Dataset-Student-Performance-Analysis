# Cross-Dataset-Student-Performance-Analysis
Using two separate Kaggle datasets to evaluate traditional vs experimental teaching methods. Models: Linear Regression, KNN classification (90% acc), Logistic Regression. Key insights on study time, sleep, class size & amp; pretest scores.

# Student Performance Prediction – Experimental vs Traditional Teaching

**Objective**  
Can data tell us whether schools should switch from traditional teaching to experimental pedagogy?  
This project uses **two completely different Kaggle datasets** to answer the exact same business question with multiple machine learning models.

**Business Problem**  
Traditional “one-size-fits-all” teaching fails to personalise support. Schools need evidence-based decisions on whether experimental methods (flipped classrooms, adaptive learning, etc.) improve exam scores and how to target interventions for at-risk students using factors like study hours, sleep, attendance, and prior performance.

**Datasets**  
| Dataset                  | Rows | Key Features                              | Target                  |
|--------------------------|------|-------------------------------------------|-------------------------|
| `student_exam_scores.csv` | 200  | hours_studied, sleep_hours, attendance, previous_scores | exam_score             |
| `test_scores.csv`         | ~2,000+ | pretest, teaching_method, n_student (class size), gender | posttest & improvement |

Both sourced from Kaggle. Cleaned in Google Colab (no missing values after preprocessing).

**Methodology**  
- **Exploratory Data Analysis** (distributions, scatter plots, correlation)  
- **Linear Regression** – to quantify impact of study hours / pretest on scores  
- **KNN Classification** (k=5) – predict “High Score” (above median)  
- **Logistic Regression** – predict “High Improvement” after intervention  

All models built with **scikit-learn** in Python (Google Colab).

**Results**  

| Model                  | Dataset | Accuracy / R² | Key Insight |
|------------------------|---------|---------------|-------------|
| Linear Regression      | DS1     | Coeff = +1.55 | +1 hour study → +1.55 exam points |
| KNN (High Score)       | DS1     | **90%**       | Study time + sleep + previous scores = excellent predictor |
| Linear Regression      | DS2     | Coeff = +0.91 | Pretest strongly predicts posttest |
| Logistic Regression    | DS2     | **65%**       | Experimental teaching method & smaller classes significantly increase odds of big improvement |

**Key Findings & Insights**  
- Experimental teaching methods clearly outperform traditional ones.  
- **Study hours, sleep, and attendance** are the strongest personal predictors (Dataset 1).  
- **Pretest score and class size** are the strongest institutional predictors (Dataset 2).  
- Students with low prior performance benefit most from targeted interventions.  
- Debt-to-income style insight: focus resources on sleep education, attendance tracking, and smaller experimental classes.

**Business Recommendation**  
- Adopt experimental pedagogy organisation-wide.  
- Implement early interventions for students with <6 study hours or poor prior scores.  
- Replace CSV files with a relational database (PostgreSQL) for scalability and real-time analytics.  
Expected outcome: 10–15% average score increase and better resource allocation.

**Limitations & Future Work**  
- Small sample in Dataset 1; some self-reported bias possible.  
- No motivation/engagement features.  

**Technologies Used**  
Python • pandas • scikit-learn • matplotlib/seaborn • Google Colab
