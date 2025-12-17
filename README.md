# Predicting Auto Claims Severity
Predicting the cost and severity of auto insurance claims using historical data. This project explores regression and other predictive modeling methods to improve risk assessment, optimize resource allocation, and reduce operational costs for insurers.

---

### 👥 **Team Members**

| Name                 | GitHub Handle | Contribution                                                                                                                                   |
|----------------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Potri Abhisri Barama | @Abhisri436   | Exploratory Data Analysis (EDA), Visualization, Data Cleaning and Feature Engineering (preprocessing pipeline), Neural Network Model Implementation and Evaluation, Documentation and Reproducibility (GitHub, README, run steps), Presentation, Overall Project Coordination |
| Rajab Begim | @Rajabb4685   | Exploratory Data Analysis (EDA), Visualization, Data Cleaning and Feature Engineering (preprocessing pipeline), Neural Network Model Implementation and Evaluation, Documentation and Reproducibility (GitHub, README, run steps), Presentation, Overall Project Coordination |

---

## 🎯 **Project Highlights**

- Developed a claims severity prediction pipeline to estimate Allstate auto claim loss from historical data, enabling smarter reserving and routing decisions.
- Built and compared multiple regression models (Linear Regression, Decision Tree, Random Forest, Neural Net, LightGBM, XGBoost) and selected XGBoost as the best performer on test data.
- Achieved strong performance with XGBoost (log scale MSE 0.2835, MAE 0.4134; original scale MAE ≈ $1,135.57, MSE ≈ $3,574,638), showing practical value for early severity estimation.
- Implemented an industry style workflow with EDA, log transforming the skewed loss target, and categorical encoding to make the dataset model ready and improve stability and accuracy.

---

## 👩🏽‍💻 **Setup and Installation**

* Clone the repo
  git clone <REPO_URL>
  cd <REPO_NAME>

* Open the notebook in Google Colab
  Colab → File → Open notebook → GitHub → paste repo link → select the notebook
  Or Upload the .ipynb from your computer

* Run the setup/imports cell
  Run the first cell with imports (it will show you if any packages are missing)

* If Colab prompts missing packages, install them
  Add a cell and run:
    !pip -q install xgboost lightgbm
  Then re run the imports cell

* Get the dataset (not included in this repo due to size)
  Download from: https://drive.google.com/file/d/1-5nvRt02hw5kDLuO2B-fvpYSLkqX7XZ-/view?usp=drive_link 
  Upload to Google Drive (recommended) or upload directly to Colab

* Mount Google Drive (if using Drive)
  Run:
    from google.colab import drive
    drive.mount('/content/drive')

* Update dataset path(s) in the notebook
  Point the file path variables to where you stored the data

* Run everything
  Colab → Runtime → Run all (runs preprocessing, training, evaluation, and generates plots/metrics)

---

## 🏗️ **Project Overview**

**Describe:**

- Break Through Tech AI Program: This project was completed as part of the Break Through Tech AI Program AI Studio experience, where our team applied industry style ML workflows to a real business problem.

- Host company + objective: In partnership with Allstate, we built a machine learning solution to predict auto insurance claim severity (loss amount) from historical claim features, with a focus on building, evaluating, and comparing multiple models.

- Scope: We conducted end to end work including EDA, data cleaning and preprocessing, feature handling for categorical variables, model training across several algorithms, and performance evaluation to select a best performing approach.

- Real world significance: Claim severity prediction supports faster, smarter insurance decisions like reserving, triage, and resource allocation.

- Potential impact: Better severity estimates can improve operational efficiency and customer experience by enabling earlier interventions and more accurate planning.

---

## 📊 **Data Exploration**

* Dataset: Allstate auto claims severity dataset (tabular CSV). The target is loss (claim severity). The feature set includes a mix of continuous variables and a large number of categorical variables.

* EDA focus: We explored distributions, checked basic data quality, and looked for patterns that could impact modeling (skew, scale differences, and categorical feature behavior).

* Preprocessing approach:
  * Confirmed the dataset structure and cleaned/standardized inputs for modeling.
  * Applied a log transform to the target because loss is heavily right skewed, which helps models learn more stable patterns.
  * Used one hot encoding for categorical variables so models can use them effectively.

* Key insights: The loss distribution is highly skewed, and transforming it improves training stability and evaluation. Both continuous and categorical features contribute meaningfully depending on the model.

* Challenges + assumptions:
  * Since features are anonymized, we focused on strong modeling and evaluation rather than domain interpretation of individual features.

**Visualizations:**

* <img width="446" height="404" alt="image" src="https://github.com/user-attachments/assets/8c846943-0514-43fa-a7ec-872dca5f245c" />
* <img width="406" height="358" alt="image" src="https://github.com/user-attachments/assets/15ae8b8a-d696-403d-b04b-9d05085350be" />
* <img width="1298" height="1154" alt="image" src="https://github.com/user-attachments/assets/1c708191-5dc7-4005-9a8f-3e94eaf96f0e" />

---

## 🧠 **Model Development**

* Models used: Linear Regression, Decision Tree, Random Forest, LightGBM, XGBoost, and a Neural Network (regression).

* Training setup: We trained on a train split and evaluated on a held out test set. Because the target (loss) is skewed, we modeled log(loss) and reported metrics on both the log scale and original dollar scale.

* Evaluation metrics: Mean Squared Error (MSE) and Mean Absolute Error (MAE), with model comparison across the same split.

* Baseline performance: Linear Regression served as the baseline, then we compared tree based ensembles and a neural net to measure improvement.

* Feature handling/selection: Categorical variables were one hot encoded, and we relied on model based feature importance (from tree models) to understand influential features rather than manual feature selection.

* Hyperparameter tuning: We did light tuning by adjusting key model parameters (for example tree depth, number of estimators, learning rate) and selected the best performing configuration based on validation/test metrics.

---

## 📈 **Results & Key Findings**

* Performance metrics: We evaluated regression performance using MAE and MSE. Because loss is highly skewed, we tracked metrics on log(loss) and also converted back to dollars to interpret real world impact.

* How the model performed: After comparing multiple models, XGBoost was our best performer, beating simpler baselines and providing the most reliable results on the held out test set. On the original dollar scale, the model achieved an MAE around $1.1K, which suggests the predictions are reasonably close for many claims while still being challenged by extreme high loss cases.

* Fairness insights: We discussed fairness as a key consideration for insurance modeling and reviewed whether performance appeared consistent across different groups. Since the dataset is anonymized and does not include direct protected attributes, we focused on overall robustness and monitoring for potential bias signals, and we recommend running subgroup error analysis if group labels become available.

**Visualizations:**
* <img width="1344" height="874" alt="image" src="https://github.com/user-attachments/assets/3ebfe15f-5908-427e-a576-8a6dddad6157" />
* <img width="1400" height="872" alt="image" src="https://github.com/user-attachments/assets/1caa4423-6d83-4313-8bef-955d01b9f6a7" />

---

## 🚀 **Next Steps**

* Limitations: Our target (loss) is highly skewed, so extreme high loss claims are harder to predict and can drive error. The dataset also has many categorical features, which increases dimensionality after encoding and can impact efficiency and generalization.

* With more time/resources: I would do deeper hyperparameter tuning, stronger cross validation, and more focused error analysis to understand where the model performs best vs struggles (especially on high loss cases).

* Additional techniques/datasets to explore: I would try target encoding for high cardinality categoricals and log plus custom loss functions for tail behavior. If available, I would incorporate more detailed claim level features (timing, location, repair or injury indicators) and run subgroup performance checks for fairness and stability.

---

## 📝 **License**

This project is licensed under the MIT License.

---

## 🙏 **Acknowledgements**

Thank your Challenge Advisor, host company representatives, TA, and others who supported your project.
