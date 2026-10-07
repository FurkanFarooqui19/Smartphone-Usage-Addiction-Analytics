# Smartphone Usage & Addiction Analytics

## Project Overview

This project analyzes smartphone usage patterns and explores their relationship with a binary smartphone addiction label. The analysis is implemented in a Jupyter notebook using the included dataset.

## Objective

The objective is to explore usage behavior, visualize relationships between smartphone activity and addiction, and provide a simple machine-learning prediction interface.

## Dataset and Important Features

The dataset contains 7,500 user records with fields covering:

- Demographics: `age`, `gender`
- Usage: `daily_screen_time_hours`, `social_media_hours`, `gaming_hours`, `work_study_hours`, `notifications_per_day`, `app_opens_per_day`, `weekend_screen_time`
- Context: `sleep_hours`, `stress_level`, `academic_work_impact`
- Target-related fields: `addiction_level`, `addicted_label`

## Target and Model

The classification target is `addicted_label`:

- `0 = Not Addicted`
- `1 = Addicted`

The notebook uses an existing `DecisionTreeClassifier` for addiction prediction. Its trained input features are `age`, `daily_screen_time_hours`, and `sleep_hours`.

## Visualizations and UI

The notebook includes:

- **Screen Time vs Addiction:** compares `daily_screen_time_hours` with `addicted_label`.
- **Correlation Heatmap:** displays correlations among numerical dataset columns.
- **Gradio UI:** accepts smartphone usage inputs and presents a user-friendly result as **🟢 Not Addicted** or **🔴 Addicted**.

## Technologies

Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, and Gradio.

## Project Structure

```text
.
├── README.md
├── Smartphone_Usage_Analytics.ipynb
└── Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv
```

## Installation and Running

From the project directory, install the required packages:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn gradio jupyter
```

Open and run `Smartphone_Usage_Analytics.ipynb` with Jupyter, JupyterLab, or VS Code. Keep the CSV file in the same directory as the notebook so it can be loaded by the analysis.

## Disclaimer

This project is for educational purposes only. Its predictions are not medical or clinical diagnoses and should not be used as a substitute for professional advice.
