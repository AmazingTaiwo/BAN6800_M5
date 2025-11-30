# BAN6800_M5
# BAN6800 Milestone 2: Business Analytics Model Results Communication
## 📘 README: Business Analytics Model
#  Project: Databricks-Enabled Procurement Analytics Optimization
#  Author: Taiwo Babalola
#  Institution: Nexford University
#  Dataset: abc_dw_gl_pr_po_kpi.csv (Gold Layer)

#  📌 Project Overview

    This repository contains all work completed for Milestone 1 and Milestone 2 of the Nexford University Business Analytics Project.
    The goal is to optimize the Purchase Requisition (PR) → Purchase Order (PO) procurement cycle at ABC Logistics Limited by enabling predictive insights using Databricks and machine        learning.

    The dataset used is the Gold Layer output from the Databricks Lakehouse pipeline, which integrates and transforms SAP S/4HANA procurement data into a clean, analytics-ready form.

#  Module 4: Builds two machine learning models:
#  Classification Model – Predict whether a procurement process will breach SLA.
#  Regression Model – Predict PR→PO cycle time (business days).
    Both models use mandatory business dimensions (company code, plant, document type, vendor country) to ensure clarity for non-technical stakeholders.

#  📂 Repository Structure
      /project/
      │
      ├── data/
      │   └── abc_dw_gl_pr_po_kpi.csv             # Gold Layer dataset
      │
      ├── notebooks/
      │   ├── BAN6800_Module 4_Assignment_ Exploratory_Data_Analytics.ipynb        # Module 4 Exploratory Data Analysis
      │   └── BAN6800_Module 4_Assignment_ Business_Analytics_Model.ipynb          # Module 4 modeling notebook
      │
      ├── images/
      │   └── charts_and_visuals/                 # Feature importance, ROC, confusion matrix, etc.
      │
      └── README.md                                # This file

#  📊 Dataset Description (Gold Layer)
      The dataset represents a fully cleaned and integrated procurement fact table, engineered through Databricks Bronze → Silver → Gold layers.
      Key fields include:
        - Procurement Dates (Business Process)
        - pr_creationdate
        - pr_approveddate
        - po_createdon
        - po_approvaldate
        - Engineered KPIs
        - pr_to_po_ageing (business days)
        - pr_approval_ageing
        - po_approval_ageing
        - sla_breach_flag
        - record_type (PR_ONLY, PO_ONLY, PR_PO_MATCHED)

#  Mandatory Dimensions
    -pr_companycode
    - po_companycode
    - pr_plant
    - po_plant
    - po_purchasingdoctype
    - po_countrykey
    - Other Business Fields
    - Order quantity
    - Net amount
    - Vendor classification
    - Material group and type
    This is the final cleaned dataset used for predictive modeling.

#  🧹 Data Cleaning & Preparation
      Performed in Databricks via Lakehouse architecture:
        ✔ Bronze Layer
          - Raw SAP extracts loaded with Auto Loader
          - CSV ingestion with schema enforcement
        ✔ Silver Layer
          - Data trimming and standardization
          - SAP date format conversion (YYYYMMDD → DateType)
          - Removal of deleted/cancelled PR/PO lines
          - Column renaming and normalization
        ✔ Gold Layer
          - Full outer join between PR and PO
          - Business day calculation (Sun–Thu working week)
          - SLA flags and KPI creation
      Record classification (PR_ONLY, PO_ONLY, MATCHED)
  The Gold dataset is exported for Modeling.

#  🤖  Business Analytics Model Development
       This notebook implements:
          1. SLA Breach Classification Model
            - Goal: Predict whether a procurement item will exceed SLA.
            - Algorithm: Random Forest Classifier
          2. Features Used:
              👉 Mandatory Business Dimensions
                  - po_companycode
                  - pr_companycode
                  - po_plant
                  - pr_plant
                  - po_purchasingdoctype
                  - po_countrykey
              👉 Numeric KPIs
                  - pr_approval_ageing
                  - po_approval_ageing
                  - pr_orderqty
                  - po_orderquantity
                  - po_netamount
                  - Evaluation Metrics:
                  - Accuracy
                  - Precision
                  - Recall
                  - F1-score
                  - ROC-AUC
                  - Confusion Matrix
                  - ROC Curve
          This supports early risk identification and intervention to avoid delays.

#  PR→PO Cycle Time Regression Model
    - Goal: Predict the number of business days required from PR → PO.
    - Algorithm: Random Forest Regressor
      Features:
        - Same mandatory dimensions
        - Numeric KPIs
        - Additional workflow attributes (PR document type, purchasing group)
      Evaluation Metrics:
        - Mean Absolute Error (MAE)
        - Root Mean Squared Error (RMSE)
         - R²
         - Actual vs Predicted Scatter Plot
    This supports forecasting, planning, and resource alignment.

#  📈 Business Insights Extracted
      Using grouped summaries:
        🏢 By Company Code
            Helps identify business units with the longest cycle times.
        🏭 By Plant
            Highlights operational units causing approval delays.
        📄 By Document Type
            Service POs and framework orders take the longest to approve.
        🌍 By Vendor Country
            International vendors have significantly higher cycle times.
        These insights directly support the goal of reducing PR→PO cycle time by 25%.

#  🚀 How to Run the Notebook
      Clone this repository:
          - git clone https://github.com/AmazingTaiwo/BAN6800_M4.git
      Install dependencies:
        - pip install pandas numpy scikit-learn matplotlib
        - Open Jupyter Notebook:
      jupyter notebook
        - Run BAN6800_Module 4_Assignment_ Exploratory_Data_Analytics.ipynb
        - Run BAN6800_Module 4_Assignment_ Business_Analytics_Model_new.ipynb

#  🎯 Deliverables for Submission
      - Cleaned and integrated dataset stored in GitHub
      - EDA notebook explaining data quality and preparation
      - Full modeling notebook**
          - Classification + Regression results
          - Visualizations (ROC curve, confusion matrix, feature importances)
          - README documenting everything
          - Organized datasets and code

#  GitHub repository link
    - URL: https://github.com/AmazingTaiwo/BAN6800_M4.git
#  Power BI
    - Download PowerBi Desktop and install on your PC 
    - Open the Dashoarcd "BAN6800 Milestone 2 -  Assignment - Databricks-Enabled Procurement Analytics Optimization Project.pbix" with     powerBI desktop application.
 #     Page
       - Actual Procurement Ageing Before Modeling
       - PR to PR Prediction
       - Service Level Performance Prediction






