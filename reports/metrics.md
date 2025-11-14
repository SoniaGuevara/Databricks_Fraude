# Métricas del Modelo — Detección de Fraude

Modelo entrenado: **Logistic Regression (Spark MLlib)**  
Dataset: Silver (284.807 transacciones)

## 📈 Métricas principales

- **AUC ROC:** 0.95
- **AUC PR:** 0.66
- **Precision (fraude):** 0.84
- **Recall (fraude):** 0.59
- **F1-score:** 0.69

## 📌 Interpretación

- **AUC alto (0.95):** excelente separación entre fraude y no fraude.
- **Precision alto:** pocas falsas alarmas.
- **Recall moderado:** se escapan algunos fraudes (normal en datasets desbalanceados).
- **F1 balanceado:** buen compromiso entre precisión y recall.
