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
