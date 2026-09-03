# AI Workforce Impact Analysis

A data-driven analysis of how artificial intelligence is influencing employment, automation risk, career opportunities, salaries, and workforce trends.

## Overview

The rapid adoption of Artificial Intelligence is changing the way organizations operate and reshaping the skills and roles required across industries.

This project analyzes the relationship between AI adoption, automation risk, technology-sector layoffs, career safety, and salary trends using publicly available datasets.

The project combines exploratory data analysis, feature engineering, statistical analysis, data visualization, and machine learning to investigate how AI-related factors may influence workforce outcomes.

## Objectives

The project aims to:

* Analyze AI adoption and automation risk across job roles and industries.
* Investigate workforce and technology-sector layoff patterns.
* Construct an AI Disruption Score using multiple workforce indicators.
* Categorize careers into Low, Medium, and High Risk groups.
* Analyze relationships between AI disruption, automation risk, and salaries.
* Build a machine learning model for career-safety risk classification.
* Build a baseline regression model for salary prediction.
* Use statistical analysis to examine AI disruption among Data Science roles.
* Communicate findings through data visualizations and quantitative metrics.

## Datasets

### Dataset 1 — AI-Powered Job Market Insights

Contains job-market information including:

* Job title
* Industry
* Company size
* Location
* AI adoption level
* Automation risk
* Required skills
* Salary
* Remote-friendliness
* Job growth projection

The dataset contains **500 job-market records**.

### Dataset 2 — Tech Layoffs

Contains technology-industry layoff information including:

* Company
* Location
* Region
* Country
* Number of employees laid off
* Layoff percentage
* Industry
* Funding
* Company size before and after layoffs
* Year
* Geographic information

The dataset contains **2,412 layoff records**.

### Combined Analysis Dataset

The two datasets are standardized by industry and aggregated before being combined with the job-market data.

The resulting analytical dataset contains **500 records and 18 features**.

## Methodology

The project follows an end-to-end data analysis and machine learning workflow.

### 1. Data Collection

Publicly available job-market and technology-layoff datasets were collected and loaded into Pandas DataFrames.

### 2. Data Cleaning

The project handles:

* Missing numerical values
* Inconsistent industry names
* Industry naming variations across datasets
* Data type and formatting inconsistencies

Missing numerical values in the layoffs dataset are handled using median imputation for selected variables, while missing funding values are replaced with zero.

### 3. Industry Standardization

Industry categories from the two datasets are mapped into common industry groups such as:

* Technology
* Financial Services
* Healthcare
* Retail
* Education
* Entertainment
* Transportation
* Manufacturing
* Telecommunications

This enables industry-level comparison between job-market and layoff data.

### 4. Feature Engineering

Industry-level workforce indicators are calculated, including:

* Total layoffs
* Average layoff percentage
* Number of layoff events
* Average funding raised

An ordinal `Risk_Score` is created from the original automation-risk categories:

| Automation Risk | Risk Score |
| --------------- | ---------: |
| Low             |          1 |
| Moderate        |          2 |
| High            |          3 |

An `AI_Disruption_Score` is then calculated using percentile ranks of:

* Automation risk
* Total layoffs
* Average layoff percentage

The resulting score is used to categorize careers into:

* Low Risk
* Medium Risk
* High Risk

A `Salary_Per_Risk` feature is also derived to compare salary levels relative to automation risk.

## Exploratory Data Analysis

The project performs exploratory analysis across job roles, industries, salaries, AI adoption, automation risk, workforce disruption, and layoff trends.

Analysis includes:

* Descriptive statistics
* Distribution analysis
* Correlation analysis
* Skewness and kurtosis
* Industry-level comparisons
* Career-risk analysis
* Salary analysis
* Data Science career analysis

Visualizations are created using Python visualization libraries to communicate patterns and relationships in the data.

## Statistical Analysis

A hypothesis test is performed on the AI Disruption Score of Data Science roles.

### Hypotheses

**H₀:** Mean AI Disruption Score of Data Science roles = 0.5

**H₁:** Mean AI Disruption Score of Data Science roles ≠ 0.5

The analysis produced:

* Sample mean: **0.4847**
* Population mean under H₀: **0.5**
* Sample standard deviation: **0.1611**
* Sample size: **11**
* Z-statistic: **-0.3146**
* p-value: **0.753054**
* Significance level: **0.05**

The analysis therefore fails to reject the null hypothesis at the 5% significance level.

## Machine Learning

### Career Safety Classification

A machine learning workflow is used to classify careers into:

* High Risk
* Medium Risk
* Low Risk

The classification experiment uses features including:

* AI Disruption Score
* Automation Risk
* AI Adoption Level
* Salary
* Risk Score

The recorded evaluation uses an 80:20 train-test split.

### Results

| Metric             | Result |
| ------------------ | -----: |
| Total Samples      |     78 |
| Training Samples   |     62 |
| Testing Samples    |     16 |
| Accuracy           | 93.75% |
| Weighted Precision | 95.83% |

A confusion matrix is also generated to evaluate classification performance across the three career-safety categories.

> **Note:** Because the classification experiment uses a relatively small evaluation set, the reported metrics should be interpreted cautiously and would benefit from cross-validation and evaluation on a larger dataset.

## Salary Prediction

A baseline Linear Regression model is developed to investigate whether workforce disruption indicators can explain salary variation.

Features include:

* AI Disruption Score
* Risk Score
* Automation Risk
* AI Adoption Level
* Total Layoffs
* Average Layoff Percentage

### Results

| Metric |   Result |
| ------ | -------: |
| R²     |  -0.2330 |
| MAE    | ~$19,205 |
| RMSE   | ~$25,238 |

The negative R² indicates that this baseline linear model does not generalize well to the salary prediction task. This provides an important limitation of the current approach and suggests that additional features, nonlinear models, larger datasets, and stronger validation would be useful for future iterations.

## Key Outputs

The project produces analysis covering:

* AI adoption patterns
* Automation risk
* Industry-level layoffs
* Career safety categorization
* AI disruption scoring
* Salary relationships
* Data Science career trends
* Statistical hypothesis testing
* Career-risk classification
* Salary prediction
* Confusion matrix analysis
* Feature coefficient analysis

## Project Structure

```text
AI-Workforce-Impact/
│
├── AI-Disruption-Index.ipynb
│   └── Complete analysis, visualization,
│       statistical testing and ML workflow
│
├── README.md
│   └── Project documentation
│
└── .gitignore
```

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* Jupyter Notebook
* Google Colab

## Machine Learning & Data Science Concepts

This project demonstrates practical experience with:

* Data cleaning
* Missing-value handling
* Data transformation
* Feature engineering
* Exploratory Data Analysis
* Statistical analysis
* Hypothesis testing
* Feature encoding
* Feature scaling
* Linear Regression
* Classification
* Train-test splitting
* Model evaluation
* Accuracy
* Precision
* Confusion Matrix
* MAE
* RMSE
* R²
* Data visualization

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Sakshi-0077/AI-Workforce-Impact.git
cd AI-Workforce-Impact
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
AI-Disruption-Index.ipynb
```

### 4. Run the notebook

Execute the notebook cells sequentially.

The current notebook uses file-upload functionality for the input datasets, so the required CSV files must be provided when prompted.

## Future Improvements

Potential improvements include:

* Replace notebook-based file uploads with a reproducible data pipeline.
* Add a dedicated Streamlit dashboard.
* Automate dataset acquisition and preprocessing.
* Apply cross-validation for more reliable model evaluation.
* Compare multiple classification algorithms.
* Perform systematic hyperparameter tuning.
* Address class imbalance where applicable.
* Increase dataset size for more reliable generalization.
* Add explainable AI techniques such as feature importance and SHAP.
* Deploy the analysis as an interactive web application.
* Add automated testing and CI/CD.
* Separate data processing, modeling, visualization, and application layers.

## Limitations

* The analysis depends on publicly available datasets.
* Dataset coverage may not fully represent the global workforce.
* Some workforce relationships are observational and should not be interpreted as causal relationships.
* The classification experiment uses a relatively small test set.
* The salary regression baseline performs poorly, indicating that additional features and improved modeling are required.
* The AI Disruption Score is a constructed analytical metric and should be interpreted as an exploratory indicator rather than an official measure of career risk.

## Conclusion

This project demonstrates an end-to-end approach to analyzing the impact of AI on workforce dynamics.

By combining job-market information with technology-sector layoff data, the project creates derived workforce indicators and investigates their relationship with career risk and salary.

The project also extends beyond exploratory analysis by applying statistical testing and machine learning to classify career safety and establish a baseline for salary prediction.

The analysis highlights both the potential of machine learning for workforce analytics and the importance of data quality, feature design, validation, and cautious interpretation when working with real-world datasets.

## License

This project is intended for educational and research purposes.

---

**Author:** Sakshi Shah
**GitHub:** Sakshi-0077
