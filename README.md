# 🔋 Predictive Maintenance for Electric Vehicle Battery Sensors

## 📖 Project Description
This project applies **Machine Learning** techniques to predict failures in electric vehicle battery cells using synthetic sensor data.  
The goal is to anticipate potential failures and optimize maintenance, reducing risks and operational costs.

---

## 📊 Dataset
- **Source:** Synthetic, generated with `src/generate_data.py`  
- **Main variables:**
  - `voltage_mean`: Average cell voltage [V]
  - `current_hv`: High-voltage battery current [A]
  - `capacity_cell1/2/3`: Capacity of each cell [Ah]
  - `temp_battery`: Battery temperature [°C]
  - `failure`: 0 = no failure, 1 = failure
- **Rows:** 50,000  
- **Notes:** Failure distribution ~2% of total.

---

## 🔍 Key EDA Insights
- Visualization of the **failure distribution**: most samples show no failure.
- **Variables correlated with failure**:
  - Low average voltage (`voltage_mean`)
  - High HV current (`current_hv`)
  - Low cell capacities (`capacity_cell1/2/3`)
  - High battery temperature (`temp_battery`)
- **Outliers and inconsistent values** were detected and handled during preprocessing.
- EDA Notebook: [`EDA_Predictive_Maintenance.ipynb`](notebooks/EDA_Predictive_Maintenance.ipynb)

---

## 🛠️ Technologies Used
- Python 3.10
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Joblib

---

## 📂 Project Structure
```
predictive-maintenance-ev/
├── data/               # Generated datasets (CSV)
├── results/            # Trained models and plots
├── src/                # Python scripts
│   ├── generate_data.py
│   ├── preprocessing.py
│   ├── train_model.py
│   └── evaluate.py
├── notebooks/          # EDA and visualization notebooks
├── requirements.txt
└── README.md
```

---

## ⚙️ Installation & Execution
1. Create a virtual environment:
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# mac/linux
# source venv/bin/activate
pip install -r requirements.txt
```

2. Generate synthetic dataset:
```bash
python src/generate_data.py
```

3. Train the model:
```bash
python src/train_model.py
```

4. Evaluate the model and generate confusion matrix:
```bash
python src/evaluate.py
```

---

## 🚀 Preliminary Results
- Model: RandomForestClassifier (optimized with GridSearchCV)  
- Metrics on test set:
  - **F1-score:** ~0.85  
  - **Accuracy:** ~0.98  
- Confusion matrix saved in `results/confusion_matrix.png`

---

## 🔮 Next Steps
- Replace RandomForest with a **neural network** (TensorFlow or PyTorch).  
- Integrate real battery datasets if available from EV systems.

---

## 👨‍💻 Author
- Jordi Moreso – [LinkedIn](https://www.linkedin.com/in/tuusuario/)  
- AI project for **Machine Learning and Predictive Maintenance** in EV batteries.
