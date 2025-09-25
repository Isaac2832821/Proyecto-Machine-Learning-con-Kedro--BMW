# 🚗 Machine Learning con Kedro – BMW

## 📌 Descripción
Este proyecto implementa un flujo completo de **Machine Learning** siguiendo la metodología **CRISP-DM**, utilizando el framework **Kedro**.  

El objetivo principal es **predecir la clasificación de ventas de autos BMW** a partir de sus características: modelo, año, motor, combustible, transmisión, kilometraje y precio.  

Se trabajan tres datasets principales (`bmw_classification`, `bmw_sales`, `bmw_used`) que atraviesan un proceso de **limpieza, preparación, entrenamiento y evaluación** de un modelo de clasificación supervisada.

---

## 📂 Estructura del Proyecto
machine-learning-con-kedro---franco-bmw/
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

1. **bmw_classification.csv**  
   Contiene información detallada de modelos BMW con sus características y clasificación de ventas.  
   **Columnas principales**:  
   - `Model`, `Year`, `Region`, `Color`, `Fuel_Type`, `Transmission`, `Engine_Size_L`, `Mileage_KM`, `Price_USD`, `Sales_Volume`, `Sales_Classification`

2. **bmw_sales.csv**  
   Ventas históricas por modelo y región.  

3. **bmw_used.csv**  
   Información de autos usados (kilometraje, precio, tipo de combustible, etc.).  

---

## ⚙️ Pipelines

### 🔹 Data Engineering
- Limpieza de `bmw_classification`, `bmw_sales`, `bmw_used`.  
- Genera datasets intermedios (`*_clean.csv`) en `data/02_intermediate/`.

### 🔹 Data Science
1. **split_data** → Divide datos en train/test aplicando *One-Hot Encoding*.  
2. **train_model** → Entrena un modelo de clasificación (**LogisticRegression**).  
3. **evaluate_model** → Calcula la métrica de **accuracy** y guarda resultados.  

---

## 🚀 Ejecución

### 1. Crear entorno virtual
```bash
python -m venv venv
.\venv\Scripts\activate
pip install -r src/requirements.txt

