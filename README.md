# My-Twelve-Repository-
Build a Model Evaluation Dashboard (Accuracy, Precision, Recall, F1)
import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from utils import (
    load_data,
    train_models,
    evaluate_models,
    plot_confusion_matrix,
    plot_roc_curve
)

# Page Config
st.set_page_config(
    page_title="Model Evaluation Dashboard",
    layout="wide"
)

st.title("📊 Model Evaluation Dashboard")

st.write("""
This dashboard compares multiple Machine Learning models using:
- Accuracy
- Precision
- Recall
- F1-score
""")

# Load Dataset
df = load_data()

st.subheader("📁 Dataset Preview")
st.dataframe(df.head())

# Train Models
models, X_test, y_test = train_models(df)

# Evaluate Models
results_df, predictions = evaluate_models(models, X_test, y_test)

# Show Table
st.subheader("📊 Model Comparison Table")
st.dataframe(results_df)

# Bar Chart
st.subheader("📈 Metrics Comparison Chart")

fig, ax = plt.subplots(figsize=(10, 6))

results_df.set_index("Model").plot(
    kind="bar",
    ax=ax
)

plt.ylabel("Score")
plt.xticks(rotation=0)

st.pyplot(fig)

# Model Selection
st.subheader("🔍 Select Model for Detailed Evaluation")

selected_model = st.selectbox(
    "Choose a Model",
    results_df["Model"]
)

selected_row = results_df[
    results_df["Model"] == selected_model
]

st.write("### 🧠 Detailed Metrics")

col1, col2 = st.columns(2)

with col1:
    st.metric(
        "Accuracy",
        f"{selected_row['Accuracy'].values[0]:.2f}"
    )

    st.metric(
        "Precision",
        f"{selected_row['Precision'].values[0]:.2f}"
    )

with col2:
    st.metric(
        "Recall",
        f"{selected_row['Recall'].values[0]:.2f}"
    )

    st.metric(
        "F1 Score",
        f"{selected_row['F1 Score'].values[0]:.2f}"
    )

# Confusion Matrix
st.subheader("🔥 Confusion Matrix")

fig_cm = plot_confusion_matrix(
    y_test,
    predictions[selected_model],
    selected_model
)

st.pyplot(fig_cm)

# ROC Curve
st.subheader("📉 ROC Curve")

fig_roc = plot_roc_curve(
    y_test,
    predictions[selected_model],
    selected_model
)

st.pyplot(fig_roc)

# Download Results
st.subheader("⬇ Export Results")

csv = results_df.to_csv(index=False)

st.download_button(
    label="Download Metrics CSV",
    data=csv,
    file_name="model_metrics.csv",
    mime="text/csv"
)

st.success("Dashboard Loaded Successfully ✅")

import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from utils import (
    load_data,
    train_models,
    evaluate_models,
    plot_confusion_matrix,
    plot_roc_curve
)

# Page Config
st.set_page_config(
    page_title="Model Evaluation Dashboard",
    layout="wide"
)

st.title("📊 Model Evaluation Dashboard")

st.write("""
This dashboard compares multiple Machine Learning models using:
- Accuracy
- Precision
- Recall
- F1-score
""")

# Load Dataset
df = load_data()

st.subheader("📁 Dataset Preview")
st.dataframe(df.head())

# Train Models
models, X_test, y_test = train_models(df)

# Evaluate Models
results_df, predictions = evaluate_models(models, X_test, y_test)

# Show Table
st.subheader("📊 Model Comparison Table")
st.dataframe(results_df)

# Bar Chart
st.subheader("📈 Metrics Comparison Chart")

fig, ax = plt.subplots(figsize=(10, 6))

results_df.set_index("Model").plot(
    kind="bar",
    ax=ax
)

plt.ylabel("Score")
plt.xticks(rotation=0)

st.pyplot(fig)

# Model Selection
st.subheader("🔍 Select Model for Detailed Evaluation")

selected_model = st.selectbox(
    "Choose a Model",
    results_df["Model"]
)

selected_row = results_df[
    results_df["Model"] == selected_model
]

st.write("### 🧠 Detailed Metrics")

col1, col2 = st.columns(2)

with col1:
    st.metric(
        "Accuracy",
        f"{selected_row['Accuracy'].values[0]:.2f}"
    )

    st.metric(
        "Precision",
        f"{selected_row['Precision'].values[0]:.2f}"
    )

with col2:
    st.metric(
        "Recall",
        f"{selected_row['Recall'].values[0]:.2f}"
    )

    st.metric(
        "F1 Score",
        f"{selected_row['F1 Score'].values[0]:.2f}"
    )

# Confusion Matrix
st.subheader("🔥 Confusion Matrix")

fig_cm = plot_confusion_matrix(
    y_test,
    predictions[selected_model],
    selected_model
)

st.pyplot(fig_cm)

# ROC Curve
st.subheader("📉 ROC Curve")

fig_roc = plot_roc_curve(
    y_test,
    predictions[selected_model],
    selected_model
)

st.pyplot(fig_roc)

# Download Results
st.subheader("⬇ Export Results")

csv = results_df.to_csv(index=False)

st.download_button(
    label="Download Metrics CSV",
    data=csv,
    file_name="model_metrics.csv",
    mime="text/csv"
)

st.success("Dashboard Loaded Successfully ✅")

text,label
"I love this product",positive
"This is amazing",positive
"Very bad experience",negative
"I hate this",negative
"Excellent service",positive
"Worst purchase ever",negative
"Absolutely fantastic",positive
"Not good",negative
"Highly recommended",positive
"Terrible quality",negative

# 📊 Model Evaluation Dashboard

## 🎯 Objective
This project compares multiple Machine Learning models using evaluation metrics such as:

- Accuracy
- Precision
- Recall
- F1-score

The dashboard is built using Streamlit.

---

# 🚀 Features

✅ Model Comparison Table  
✅ Metrics Visualization  
✅ Confusion Matrix  
✅ ROC Curve  
✅ Download CSV Results  
✅ Interactive Dashboard  

---

# 🛠 Technologies Used

- Python
- Streamlit
- pandas
- scikit-learn
- matplotlib
- seaborn

---

# 📦 Installation

## 1 Clone Repository

```bash
git clone <repository_link>
cd Model_Evaluation_Dashboard
