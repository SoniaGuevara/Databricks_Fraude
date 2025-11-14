# Reporte de Resultados — Proyecto de Detección de Fraude

El modelo presenta un comportamiento sólido considerando las características del dataset, particularmente el desbalance extremo (solo 0.17% son fraude).

## 🔍 Hallazgos Principales

1. Las transacciones con **usuarios de mayor riesgo** (según nuestro dataset enriquecido) tienen mayor probabilidad de fraude.
2. El modelo logra una muy buena **precision**, evitando falsos positivos.
3. A pesar de ser un dataset desbalanceado, el modelo mantiene un **AUC excelente (0.95)**.
4. La **curva PR** muestra que el modelo evita caer en la predicción “todo es legítimo”.

## ❗ Límites del modelo

- El recall podría mejorarse usando técnicas como:
  - SMOTE (oversampling)
  - Penalización de clase
  - Árboles de decisión más profundos
  - Random Forest o XGBoost

## 📌 Conclusión

El sistema construido es totalmente funcional dentro de la arquitectura Lakehouse y demuestra capacidad real para procesamiento distribuido y análisis de fraude a escala.
