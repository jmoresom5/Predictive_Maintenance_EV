# 🔋 Predictive Maintenance for Electric Vehicle Battery Sensors

## 📖 Descripción del proyecto
Este proyecto aplica técnicas de **Machine Learning** para predecir fallos en celdas de batería de vehículos eléctricos usando datos sintéticos de sensores.  
El objetivo es anticipar posibles fallos y optimizar el mantenimiento, reduciendo riesgos y costes operativos.

---

## 📊 Dataset
- **Fuente:** Sintético, generado con `src/generate_data.py`  
- **Variables principales:**
  - `voltage_mean`: Voltaje medio de la celda [V]
  - `current_hv`: Corriente de la batería HV [A]
  - `capacity_cell1/2/3`: Capacidad de cada celda [Ah]
  - `temp_battery`: Temperatura de la batería [°C]
  - `failure`: 0 = sin fallo, 1 = fallo
- **Filas:** 50,000  
- **Notas:** Distribución de fallos ~2% del total.

---

## 🔍 EDA Destacado
- Visualización de la **distribución de fallos**: la mayoría de las muestras no presentan fallo.
- **Variables correlacionadas con fallo**:
  - Voltaje medio bajo (`voltage_mean`)
  - Corriente HV alta (`current_hv`)
  - Capacidades de celdas bajas (`capacity_cell1/2/3`)
  - Temperatura de batería alta (`temp_battery`)
- **Outliers y valores inconsistentes** detectados y considerados en el preprocesado.
- Notebook de EDA: [`EDA_Predictive_Maintenance.ipynb`](notebooks/EDA_Predictive_Maintenance.ipynb)

---

## 🛠️ Tecnologías utilizadas
- Python 3.10
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Joblib

---

## 📂 Estructura del proyecto
```
predictive-maintenance-ev/
├── data/               # Datos generados (CSV)
├── results/            # Modelos entrenados y gráficas
├── src/                # Scripts Python
│   ├── generate_data.py
│   ├── preprocessing.py
│   ├── train_model.py
│   └── evaluate.py
├── notebooks/          # Notebooks de EDA y visualización
├── requirements.txt
└── README.md
```

---

## ⚙️ Instalación y ejecución
1. Crear entorno virtual:
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# mac/linux
# source venv/bin/activate
pip install -r requirements.txt
```

2. Generar dataset sintético:
```bash
python src/generate_data.py
```

3. Entrenar modelo:
```bash
python src/train_model.py
```

4. Evaluar modelo y generar matriz de confusión:
```bash
python src/evaluate.py
```

---

## 🚀 Resultados preliminares
- Modelo: RandomForestClassifier (mejorado con GridSearchCV)  
- Métricas en test set:
  - **F1-score:** ~0.85  
  - **Accuracy:** ~0.98  
- Matriz de confusión guardada en `results/confusion_matrix.png`

---

## 🔮 Próximos pasos
- Sustituir RandomForest por una **red neuronal** (TensorFlow o PyTorch).  
- Explorar técnicas de **oversampling/SMOTE** para desbalanceo de clases.  
- Exportar modelo a **ONNX** o desplegar API con **FastAPI**.  
- Integrar análisis de batería real si se dispone de dataset del vehículo eléctrico.

---

## 👨‍💻 Autor
- Jordi Moreso – [LinkedIn](https://www.linkedin.com/in/tuusuario/)  
- Proyecto de IA para **Machine Learning y Predictive Maintenance** en baterías EV.
