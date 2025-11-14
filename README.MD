# 🌐 Sistema de Detección de Fraude con Databricks Lakehouse

**Materia:** Análisis de Datos en la Nube — UNCUYO  
**Proyecto:** Lakehouse + ML Distribuido

---

## 📚 Índice

- [🏦 Descripción General](#-descripción-general)
- [🏗️ Arquitectura del Proyecto](#️-arquitectura-del-proyecto)
- [🧪 Dataset Utilizado](#-dataset-utilizado)
- [🚀 Etapas del Proyecto](#-etapas-del-proyecto)
  - [🔶 Etapa 0 — Preparación del Entorno](#-etapa-0--preparación-del-entorno)
  - [🔶 Etapa 1 — Capa Silver](#-etapa-1--capa-silver)
  - [🔶 Etapa 2 — Machine Learning Distribuido](#-etapa-2--machine-learning-distribuido)
  - [🔶 Etapa 3 — Visualizaciones](#-etapa-3--visualizaciones)
  - [🔶 Etapa 4 — Capa Gold](#-etapa-4--capa-gold)
- [📊 Métricas del Modelo](#-métricas-del-modelo)
- [🗂️ Estructura del Repositorio](#️-estructura-del-repositorio)
- [💾 Instalación Local](#-instalación-local)
- [📌 Conclusiones](#-conclusiones)

---

## 🏦 Descripción General

Este proyecto implementa un **sistema completo de detección de fraude** utilizando:

- Apache Spark
- Delta Lake
- Databricks Lakehouse
- Algoritmos de Machine Learning distribuidos
- Visualizaciones y análisis avanzados

El objetivo es construir una arquitectura profesional de datos capaz de procesar **cientos de miles de transacciones** y detectar actividad fraudulenta.

---

## 🏗️ Arquitectura del Proyecto

```
                ┌────────────────────────────────┐
                │ Dataset Kaggle CSV             │
                └───────────────┬────────────────┘
                                │
                       (Ingesta Batch)
                                │
           ┌────────────────────▼────────────────────┐
           │                BRONZE                   │
           │ Datos crudos sin transformar            │
           └────────────────────┬────────────────────┘
                                │
                     (Limpieza + Enriquecimiento)
                                │
           ┌────────────────────▼────────────────────┐
           │                SILVER                   │
           │ Datos limpios + metadata de usuarios    │
           └────────────────────┬────────────────────┘
                                │
                       (Predicción ML)
                                │
           ┌────────────────────▼────────────────────┐
           │                 GOLD                    │
           │ Datos listos para BI / dashboards       │
           └─────────────────────────────────────────┘
```

---

## 🧪 Dataset Utilizado

**[Credit Card Fraud Detection (Kaggle)](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)**

- ✔ 284.807 transacciones
- ✔ 492 fraudes
- ✔ 30 features numéricos transformados con PCA
- ✔ Desbalanceado → ideal para ML realista

Además, se generó una **tabla adicional de usuarios** con:

- edad
- nivel de riesgo
- monto promedio
- user_id
- comportamiento simulado realista

---

## 🚀 Etapas del Proyecto

### 🔶 Etapa 0 — Preparación del Entorno

📌 **Se realizó:**

- Configuración de base de datos: `lakehouse_fraude`
- Descarga del dataset vía `kagglehub`
- Conversión CSV → Pandas → Spark
- Tabla Bronze persistida en Delta
- Tabla `ref_usuarios` generada con reglas realistas

**Reglas para clasificar riesgo:**

| Nivel | Criterio                          |
| ----- | --------------------------------- |
| ALTO  | monto_promedio > 6000 y edad < 25 |
| MEDIO | monto_promedio entre 3000 y 6000  |
| BAJO  | resto                             |

---

### 🔶 Etapa 1 — Capa Silver

**Incluyó:**

- Limpieza (tipos numéricos, nulos, duplicados)
- Enriquecimiento con metadata de usuarios
- Persistencia en tabla Silver
- Validaciones de esquema, conteo y muestras

---

### 🔶 Etapa 2 — Machine Learning Distribuido

Se entrenó un modelo con **Spark MLlib** usando:

- ✔ VectorAssembler
- ✔ Logistic Regression
- ✔ Split 80/20
- ✔ Predicciones y probabilidades

El modelo se entrenó con más de **280k filas** procesadas de forma distribuida.

---

### 🔶 Etapa 3 — Visualizaciones

**Gráficos generados automáticamente:**

- 📈 Curva ROC
- 📉 Curva Precision–Recall
- 🔢 Matriz de confusión
- 🟦 Histograma de probabilidades
- 🟧 Distribución por niveles de riesgo

---

### 🔶 Etapa 4 — Capa Gold

La **tabla GOLD** incluye:

- Predicción final
- Probabilidad de fraude
- Datos de usuario
- Monto total
- Features completos
- Nivel de riesgo
- Estructura lista para dashboards

✔ Compatible con **Databricks SQL**, **Power BI**, **Looker Studio**.

---

## 📊 Métricas del Modelo

| Métrica                | Valor   |
| ---------------------- | ------- |
| **AUC ROC**            | ⭐ 0.95 |
| **AUC PR**             | 0.66    |
| **Precision (fraude)** | 0.84    |
| **Recall (fraude)**    | 0.59    |
| **F1-score**           | 0.69    |

**Interpretación:**

- El modelo distingue bien transacciones legítimas vs fraudulentas
- Muy pocas falsas alarmas
- Se escapan algunos fraudes (recall típico en datasets desbalanceados)

---

## 🗂️ Estructura del Repositorio

```
├── notebooks/
│   ├── CreditCard_Lakehouse.ipynb
│   └── CreditCard_Lakehouse.html
├── data/
│   ├── creditcard.csv
│   └── README_data.md
├── reports/
│   ├── metrics/
│   └── charts/
├── diagrams/
│   └── lakehouse_architecture.png
├── README.md
└── requirements.txt
```

---

## 💾 Instalación Local

```bash
pip install -r requirements.txt
jupyter notebook notebooks/CreditCard_Lakehouse.ipynb
```

---

## 📌 Conclusiones

Este proyecto demuestra:

- ✅ Dominio de Big Data
- ✅ Arquitecturas modernas Lakehouse
- ✅ Procesamiento distribuido
- ✅ Modelos de Machine Learning escalables
- ✅ Visualizaciones profesionales
- ✅ Pipeline completo desde datos crudos hasta insights

**Es un trabajo totalmente apto para:**

- ✨ Portfolio
- ✨ Entrevistas técnicas
- ✨ Presentaciones académicas
