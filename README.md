# 🫀 Pipeline de Predicción de Riesgo Cardíaco y Modelado Dual (KNIME 5.12)

Pipeline de Machine Learning de grado industrial desarrollado en **KNIME Analytics Platform 5.12**, diseñado para la evaluación clínica del riesgo cardíaco, la prevención de sesgos estadísticos y la automatización de reportes ejecutivos.

---

## 📌 Resumen del Proyecto
Este proyecto implementa una arquitectura end-to-end de analítica predictiva y no supervisada. Está diseñado bajo estrictas buenas prácticas de ingeniería de datos para evitar la **fuga de datos (data leakage)** durante el preprocesamiento y optimizar KPIs de negocio orientados a la mitigación de riesgos.

---

## 🏗️ Arquitectura del Pipeline
El flujo de trabajo en KNIME se divide en cuatro fases modulares:

1. **ETL y Formato:** Ingesta de datos clínicos mediante `CSV Reader` y estandarización visual con `Color Palette Designer`.
2. **Preprocesamiento y Prevención de Sesgo:** 
   * Partición estratificada de datos (80% entrenamiento / 20% prueba).
   * Balanceo de clases mediante **SMOTE** aplicado **únicamente** sobre el conjunto de entrenamiento.
   * Escalado de variables mediante **Min-Max Normalization** (el modelo aplica las fronteras estadísticas de entrenamiento al conjunto de prueba mediante *Normalizer Apply*).
3. **Modelado Dual:**
   * **Supervisado:** *Random Forest Learner* & *Predictor* (Clasificación de riesgo binario).
   * **No Supervisado:** *k-Means Clustering* (Segmentación de perfiles biométricos ocultos).
4. **Evaluación y Reporting Automático:**
   * Auditoría de rendimiento con Matriz de Confusión (`Scorer`).
   * Validación de capacidad diagnóstica con Curva ROC y cálculo de AUC.
   * Visualización interactiva de clústeres mediante *Scatter Plot*.
   * Exportación automatizada de entregables ejecutivos vía `Excel Writer`.

---

## 📈 Resultados y KPIs del Modelo
El modelo auditado sobre el conjunto de datos de prueba puros arrojó los siguientes indicadores clave de rendimiento:

* **Exactitud Global (Accuracy):** $77.78\%$
* **Sensibilidad al Riesgo (Recall):** $83.33\%$ (Identificación de 20 de 24 casos reales de riesgo).
* **Capacidad Diagnóstica (AUC):** **$0.845$** (Excelente rendimiento en la curva ROC).

### Interpretación Analítica para Negocio
> Gracias al balanceo por **SMOTE**, el modelo prioriza la reducción de **Falsos Negativos** (casos de riesgo no detectados). Esta arquitectura es directamente extrapolable a entornos corporativos de evaluación de riesgo crediticio (*default* financiero) o fuga de clientes (*churn*), donde el costo de omitir una alerta supera con creces el costo operativo de una revisión secundaria.

---

## 📊 Evidencias y Visualizaciones

* **Matriz de Confusión:** Permitió aislar el comportamiento del modelo frente a clases desbalanceadas.
* **Curva ROC ($AUC = 0.845$):** Demuestra una sólida capacidad de separación entre clases por encima del umbral analítico estándar.
* **Gráfico de Dispersión (Scatter Plot):** Correlación de variables biométricas clave (Edad vs. Colesterol) segmentadas bajo paleta corporativa.

---

## ⚙️ Cómo Ejecutar este Proyecto
1. Descarga e instala **KNIME Analytics Platform (v5.12 o superior)**.
2. Clona este repositorio o descarga el archivo del flujo de KNIME (`.knwf`).
3. Importa el flujo en tu espacio de trabajo local de KNIME.
4. Asegúrate de actualizar la ruta del nodo **Excel Writer** apuntando a un directorio local en tu equipo para la exportación del reporte `.xlsx`.
5. Ejecuta el pipeline completo (`F7` o ejecución general).

---
*Desarrollado con rigor analítico para portafolios profesionales de Business Data Analytics.*