# HR Attrition & L&D Program Analysis

### Project Objective

This project is an end-to-end Exploratory Data Analysis (EDA) based on the [Assignment Guidelines](link-to-your-assignment-doc.docx). The objective is to analyze a real-world HR dataset to understand the key drivers of employee attrition and, specifically, to measure the business impact of the company's Learning & Development (L&D) programs.

### Dataset

The dataset used is the **HR Analytics Employee Attrition & Performance** dataset from Kaggle.
* **Source:** [https://www.kaggle.com/datasets/mahmoudemadabdallah/hr-analytics-employee-attrition-and-performance](https://www.kaggle.com/datasets/mahmoudemadabdallah/hr-analytics-employee-attrition-and-performance)
* **Structure:** This is a relational dataset. Analysis required joining a primary `DimEmployee` table with a `FactPerformanceRating` table and other dimension tables.

---

### Methodology: The 6-Phase Analysis

The project followed a structured six-phase analytical process:

1.  **Understand the Database:** Identified the relational "star schema" structure of the data.
2.  **Build Cognitive Model:** Defined primary KPIs (Attrition Rate, Training Uptake) and dimensions (Department, Tenure).
3.  **Build Logical & Physical Model:** Planned and executed the table joins in pandas to create a single, unified analysis dataframe.
4.  **Prepare the Analysis Data:**
    * Cleaned and converted data types (e.g., `HireDate` to datetime).
    * Handled duplicate entries by isolating only the *most recent performance review* for each of the 1,470 unique employees.
    * Engineered new features, such as `TenureInYears`.
    * Handled all missing (null) values.
5.  **Analyse the Data:** Performed a comprehensive EDA, including:
    * **Distribution Analysis** (e.g., histogram of training)
    * **Comparative Analysis** (e.g., attrition by department)
    * **Relation Analysis** (e.g., correlation heatmap)
    * **Trend Analysis** (e.g., attrition by tenure)
    * **Diagnosis Analysis** (e.g., attrition by manager rating)
6.  **Discover & Present Insights:** Summarized the findings into a clear, actionable data story.

---

### Key Findings & Data Story

The analysis revealed a counter-intuitive story: the company is inadvertently training its high-performing employees to leave.

#### Insight 1: L&D Training Has No Impact on Retention
The primary hypothesis that L&D programs increase loyalty was proven false.
* The correlation between training taken and attrition is **+0.04 (statistically zero)**.
* Employees who **left** (avg. 0.93 trainings) were slightly *more* trained than employees who **stayed** (avg. 0.83).

![Average Training Taken by Attrition Status](training_vs_attrition_bar.png)

#### Insight 2: We Are Losing Our High-Performers
The data contradicts the belief that unhappy or low-rated employees are the ones leaving.
* Employees who left had a **higher median manager rating** than those who stayed.
* `JobSatisfaction` also had a slight positive correlation with attrition.

![Manager Rating by Attrition Status](manager_rating_vs_attrition_boxplot.png)

#### Insight 3: Attrition is Highest in Sales & Among Newer Staff
The problem is concentrated in specific areas.
* The **Sales** department has the highest attrition rate (over 20%).
* Employees who leave have a significantly **shorter tenure** than those who stay.

![Attrition Rate by Department](attrition_by_department_bar.png)
![Employee Tenure by Attrition Status](tenure_vs_attrition_boxplot.png)

### Final Conclusion & Hypothesis

**The Core Story:** We are functioning as a "stepping stone" company. We hire good employees, they perform well (high manager ratings), and they take training. However, they are leaving within a few years, likely for better compensation or career growth that our company is not providing.

---

### Technologies Used
* **Python 3**
* **pandas** for data loading, cleaning, and manipulation (merging, joining).
* **seaborn** & **matplotlib** for data visualization (bar plots, boxplots, histograms, and heatmaps).
* **Google Colab** as the notebook environment.
