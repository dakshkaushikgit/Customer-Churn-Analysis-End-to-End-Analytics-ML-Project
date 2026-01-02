# Customer-Churn-Analysis-End-to-End-Analytics-ML-Project

## Overview
This project delivers a complete, production-style customer churn analytics and prediction solution using **SQL Server, Power BI, and Python-based machine learning**. The objective is to move beyond descriptive reporting and enable data-driven customer retention decisions by identifying churn drivers, high-risk segments, and predicting future churners.\
The solution mirrors real-world enterprise analytics workflows, covering ETL design, data validation, KPI standardization, interactive BI dashboards, and predictive modeling.

## Business Problem
Customer churn directly impacts revenue, growth, and long-term profitability—especially in highly competitive industries like telecommunications. Organizations often struggle with:
* Fragmented churn metrics across reports
* Limited visibility into churn drivers
* Reactive retention strategies instead of proactive interventions
  
This project addresses those gaps by building a ****repeatable churn monitoring and prediction pipeline****.

## Target Audience
While the dataset is telecom-focused, the methodology is industry-agnostic and applicable to:
* Telecom & utilities
* Subscription-based services
* Retail & e-commerce
* Financial services
* SaaS platforms
  
Any organization with recurring customers and transactional data can adapt this approach.

## Project Objectives
* Build an end-to-end ETL pipeline for customer churn analysis
* Standardize churn KPIs and definitions across reporting layers
* Analyze churn drivers across demographic, geographic, service, and account dimensions
* Predict future churners using machine learning
* Enable proactive, operationally actionable retention insights

## Dataset
* ~6,400 customer records<br/>
* 32 structured attributes
  * Covers demographics, services, contracts, billing, tenure, revenue, and churn reasons

## Technology Stack

### Data & ETL
* SQL Server (Staging tables, Production tables, Views)
* CSV ingestion via Import Wizard

### Analytics & Visualization
* Power BI
  * DAX measures
  * Data modeling
  * Interactive dashboards
  * Drill-throughs & tooltips
### Machine Learning
* Python
  * Pandas, NumPy
  * Scikit-learn
  * Random Forest Classification

 ## Architecture
 ```mermaid
 graph TD
    A[CSV Source] --> B[SQL Server: stg_Churn]
    B --> C{Validation and Cleaning}
    C --> D[SQL Server: prod_Churn]
    D --> E[SQL Views: Reporting & ML]
    E --> F[Power BI Dashboards]
    E --> G[Python ML Model: Random Forest]
    G --> H[Predicted Churn Outputs]
    H --> I[Power BI: Churn Prediction Dashboard]
 ```
## STEP 1 – SQL Server ETL

### Key ETL Design Decisions
* Separate staging and production tables
* Enforce primary key on Customer_ID
* Preserve data integrity while handling missing values
* Standardize categorical defaults ("None", "No", "Others")

### Data Validation
* Distinct value profiling
* Null analysis across all 32 attributes
* Revenue consistency checks
* Churn totals validated against aggregates

### Output Tables & Views
graph TD

%% Source
A[CSV Source]

%% Staging Layer
subgraph STAGING["Staging Layer"]
    B[stg_Churn]
end

%% Production Layer (highlighted)
subgraph PRODUCTION["Production Layer (Single Source of Truth)"]
    D[prod_Churn]
end

%% Semantic / Reporting Layer (highlighted)
subgraph SEMANTIC["Semantic & Reporting Layer"]
    E1[vw_ChurnData<br/>(Stayed + Churned)]
    E2[vw_JoinData<br/>(New Joiners)]
end

%% Downstream Consumers
F[Power BI Dashboards]
G[Python ML Model<br/>Random Forest]
H[Predicted Churn Outputs]
I[Power BI Churn Prediction Dashboard]

%% Flow
A --> B
B --> D
D --> E1
D --> E2
E1 --> F
E1 --> G
G --> H
H --> I

%% Styling
classDef prod fill:#e3f2fd,stroke:#1565c0,stroke-width:2px;
classDef view fill:#f1f8e9,stroke:#33691e,stroke-width:2px;

class D prod;
class E1,E2 view;


  
End-to-end customer churn analytics and prediction solution using SQL Server, Power BI, and Random Forest modelling—built to replicate enterprise-grade ETL, KPI standardisation, and retention decision workflows.
