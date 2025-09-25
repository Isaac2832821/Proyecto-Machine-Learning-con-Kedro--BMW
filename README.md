# 🚗 Machine Learning con Kedro – BMW

## 📌 Descripción
Este proyecto implementa un flujo completo de **Machine Learning** siguiendo la metodología **CRISP-DM**, utilizando el framework **Kedro**.  

El objetivo principal es **predecir la clasificación de ventas de autos BMW** a partir de sus características: modelo, año, motor, combustible, transmisión, kilometraje y precio.  

Se utilizan tres datasets principales (`bmw_classification`, `bmw_sales`, `bmw_used`) que atraviesan un proceso de limpieza, preparación, entrenamiento y evaluación de un modelo de clasificación supervisada.

---

## 📂 Estructura del Proyecto

achine-learning-con-kedro---franco-bmw/
│
├── conf/
│ └── base/
│ ├── catalog.yml # Definición de datasets
│ ├── parameters.yml # Parámetros globales (target_column, modelo, etc.)
│ └── logging.yml # Configuración de logs
│
├── data/
│ ├── 01_raw/ # Datos originales
│ ├── 02_intermediate/ # Datos limpios
│ ├── 03_primary/ # Splits de train/test
│ ├── 06_models/ # Modelos entrenados (.pkl)
│ └── 08_reporting/ # Resultados y métricas
│
├── notebooks/
│ └── analisis_resultados.ipynb # Notebook para análisis de resultados
│
├── src/
│ └── proyecto_ml/
│ ├── pipelines/
│ │ ├── data_engineering/ # Limpieza de datos
│ │ │ ├── nodes.py
│ │ │ └── pipeline.py
│ │ └── data_science/ # Split, entrenamiento y evaluación
│ │ ├── nodes.py
│ │ └── pipeline.py
│ └── pipeline_registry.py # Registro de pipelines
│
└── README.md

---

## 📊 Datasets utilizados

### **1. bmw_classification.csv**
Contiene información detallada de modelos BMW con sus características y clasificación de ventas.  

**Columnas principales:**
Model, Year, Region, Color, Fuel_Type, Transmission,
Engine_Size_L, Mileage_KM, Price_USD, Sales_Volume, Sales_Classification

### **2. bmw_sales.csv**
Ventas históricas por modelo y región.

### **3. bmw_used.csv**
Información de autos usados (kilometraje, precio, tipo de combustible, etc.).

---

## ⚙️ Pipelines

### 🔹 Data Engineering
- Limpieza de `bmw_classification`, `bmw_sales`, `bmw_used`.  
- Genera datasets intermedios (`*_clean.csv`) en `data/02_intermediate/`.

### 🔹 Data Science
- **`split_data`** → Divide datos en train/test aplicando One-Hot Encoding para variables categóricas.  
- **`train_model`** → Entrena un modelo de clasificación (`LogisticRegression`).  
- **`evaluate_model`** → Calcula la métrica de *accuracy* y guarda resultados.  

---

## 📌 Ejecución

### 1. Crear entorno virtual
```powershell
python -m venv venv
.\venv\Scripts\activate
pip install -r src/requirements.txt
correr kedro
kedro run
3. Visualizar pipelines (opcional)
kedro viz
Iniciar Jupyter Notebook
jupyter notebook
Luego abrir notebooks/analisis_resultados.ipynb.
📈 Resultados esperados

Modelo entrenado guardado en:

data/06_models/model.pkl


Métrica de accuracy guardada en:

data/08_reporting/accuracy.pkl


Posibilidad de generar un CSV con predicciones para reportes:

data/08_reporting/predicciones.csv
🛠️ Tecnologías utilizadas

Kedro → Gestión de pipelines

scikit-learn → Modelos de ML y métricas

pandas → Procesamiento de datos

Jupyter Notebook → Análisis exploratorio y validación de resultados
