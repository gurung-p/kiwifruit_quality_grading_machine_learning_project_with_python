# **Kiwifruit Quality Grading – Machine Learning Project**  
A complete end‑to‑end scikit‑learn workflow for predicting kiwifruit quality grades (A, B, C, Reject)

---

## **Project Overview**

This project builds a full machine‑learning pipeline to automatically classify the quality grade of kiwifruit using real‑world packhouse features such as **weight**, **dry matter**, **firmness**, **skin defects**, and **fruit dimensions**.  

The workflow includes:

- Exploratory Data Analysis (EDA)  
- Feature preparation  
- Model training (Random Forest, Gradient Boosting, Logistic Regression, SVM)  
- Hyperparameter tuning with GridSearchCV  
- Model comparison  
- Final model selection  
- Saving predictions and exporting results  

The dataset and prediction outputs are included in this repository.

---

## **Repository Structure**

```
├── kiwifruit_quality.csv              # Full dataset used for training
├── kiwifruit_predictions.csv          # Actual vs predicted grades from the final model
├── kiwifruit_model_1.pkl              # Saved optimised model (joblib)
├── kiwifruit_grading_ml_workflow.ipynb# Full ML workflow notebook
├── README.md                          # Project documentation
└── kiwifruit_grading_ml_workflow.png  # Workflow diagram
```

---

## **Dataset Summary**

The dataset contains **697 kiwifruit samples**, each with physical, chemical, and defect‑related measurements.  
Example fields include:

- **Weight_g**
- **Diameter_mm**
- **Length_mm**
- **DryMatter_pct**
- **Brix**
- **Firmness_kgf**
- **SkinDefects_pct**
- **ShapeIndex**
- **Grade** (Target: A, B, C, Reject)

From the dataset:

> “Weight averages around 95 g, ranging from 60–150 g… Dry Matter averages 15.5%… Skin defects range up to 27.4%.”  


The grade distribution is imbalanced, with Grade **B** being the most common and **Reject** the least represented.

---

## **Machine Learning Approach**

### **1. Data Preparation**
- Removed non‑predictive identifiers such as `FruitID`.
- Split into training and test sets using **stratified sampling** to preserve grade proportions.
- Applied **StandardScaler** inside a scikit‑learn Pipeline.

### **2. Models Evaluated**
Four models were trained and tuned:

| Model | Notes |
|-------|-------|
| Random Forest | Strong baseline, handles noise well |
| Gradient Boosting | High accuracy, captures subtle patterns |
| Logistic Regression | Linear baseline |
| Support Vector Machine | Effective for complex boundaries |

Each model was optimised using **GridSearchCV** with cross‑validation.

### **3. Model Selection**
The best model achieved:

> **Overall Accuracy: 0.98**  


The confusion matrix showed near‑perfect performance, with:

> “No Reject fruit was ever misclassified… Most mistakes occurred between B and C.”  


### **4. Feature Importance**
For tree‑based models, the most influential features were:

- **Weight_g**  
- **DryMatter_pct**  
- **SkinDefects_pct**

As noted:

> “Weight and Dry Matter carry most of the predictive power for the dataset.”  


---

## **Results**

### **Classification Performance**
- Accuracy: **98%**
- High precision and recall across all classes
- Excellent performance on minority classes (A and Reject)

### **Confusion Matrix Insights**
- Perfect classification for **A** and **Reject**
- Minor confusion between **B** and **C**, which is expected due to visual similarity

### **Prediction Output**
A CSV file (`kiwifruit_predictions.csv`) contains:

- Actual grade  
- Predicted grade  
- Whether the prediction was correct  

## **Model Saving**

The final optimised model is saved as:

```
kiwifruit_model_1.pkl
```

This allows seamless reuse for deployment or further experimentation.

---

## **Workflow Diagram**

The repository includes a full workflow diagram:

```
kiwifruit_grading_ml_workflow.png
```

This visual summarises the entire ML pipeline from raw data to final predictions.

