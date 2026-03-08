# TelecomX-Churn-Prediction-ivanmmarcial

# 📡 Telecom X — Predicción de Abandono de Clientes (Churn) · Parte 2

**Challenge 2 · Data Science · Oracle Next Education + Alura Latam**

---

## 📌 Tabla de Contenidos

- [Sobre el Proyecto](#-sobre-el-proyecto)
- [Relación con la Parte 1](#-relación-con-la-parte-1)
- [Metodología](#️-metodología)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Modelos Implementados](#-modelos-implementados)
- [Resultados y Hallazgos](#-resultados-y-hallazgos)
- [Conclusiones Estratégicas](#-conclusiones-estratégicas)
- [Autor](#-autor)

---

## 📝 Sobre el Proyecto

**Objetivo:** Desarrollar un sistema predictivo capaz de identificar con anticipación qué clientes de **Telecom X** tienen mayor probabilidad de cancelar su servicio (*churn*), analizando los factores críticos que impulsan esta decisión.

Este proyecto aplica técnicas de **Machine Learning y análisis estadístico** sobre un dataset de **7.267 clientes**, con el objetivo de transformar datos históricos en **estrategias de retención proactivas**.

---

## 🔗 Relación con la Parte 1

Este notebook continúa el proceso de **ETL (Extracción, Transformación y Carga)** desarrollado en la Parte 1. Se toma como punto de partida el dataset previamente procesado, que incluye:

- Tratamiento de valores nulos e inconsistencias  
- Traducción y estandarización de columnas  
- *Feature engineering* inicial (`Cuentas_Diarias`, posteriormente eliminada por redundancia)

---

## 🏗️ Metodología

El flujo de trabajo se dividió en **cuatro fases técnicas**.

### 🛠️ Fase 1 — Preprocesamiento y Limpieza Final

- **Encoding:** Aplicación de *One-Hot Encoding* para variables categóricas  
- **Limpieza de nombres:** Normalización de etiquetas de columnas (eliminación de espacios y puntos) para compatibilidad con modelos  
- **Gestión de redundancia:** Eliminación de variables con correlación perfecta (*multicolinealidad*)  
- **Escalado:** Uso de `StandardScaler` posterior al *train-test split* para evitar **data leakage**

### 📊 Fase 2 — Análisis de Correlación

- Identificación de variables con mayor influencia sobre el **churn**
- Visualización de patrones clave:
  - Impacto del servicio de **fibra óptica**
  - **Tipo de contrato**
  - **Antigüedad del cliente**

### 🤖 Fase 3 — Modelado y Evaluación

- División del dataset **80/20 con estratificación**
- Modelos implementados:
  - **Modelo A:** Regresión Logística (*baseline vs. balanced*)
  - **Modelo B:** Random Forest con *tuning* de hiperparámetros para reducir **overfitting**

### 📋 Fase 4 — Interpretación de Resultados

- Análisis de **coeficientes** y **feature importance**
- Elaboración de **recomendaciones estratégicas basadas en datos**

---

## 📁 Estructura del Repositorio

```
TelecomX-Churn-Prediction-ivanmmarcial/
│
├── 📓 TelecomX_parte2_Latam.ipynb         # Notebook principal de análisis
├── 📊 datos_tratados.csv                  # Dataset original
├── 📊 telecom_churn_final_procesado.csv   # Dataset procesado y estandarizado
└── 📄 README.md                           # Documentación del proyecto
```


---

## 🤖 Modelos Implementados

### 1️⃣ Regresión Logística (Modelo ganador)

- **Ajuste:** `class_weight='balanced'`
- **Desempeño:** Recall **0.81**, detectando aproximadamente **8 de cada 10 clientes en riesgo**
- **Ventaja:** Alta **interpretabilidad estadística** de los coeficientes

### 2️⃣ Random Forest (Tuned)

- **Ajuste:** `max_depth=7`, `min_samples_leaf=10`
- **Desempeño:** Corrección de **overfitting inicial**  
  *(0.99 train → 0.76 train)*  
  logrando un **Recall de 0.79**
- **Ventaja:** Identificación robusta de la **importancia relativa de variables no lineales**

---

## 📊 Resultados y Hallazgos

- **El factor tiempo:**  
  El riesgo de abandono es máximo en el **primer mes** (380 bajas). Superar los **primeros 90 días** incrementa significativamente la probabilidad de permanencia.

- **Vulnerabilidad contractual:**  
  Los contratos **mes a mes** presentan un riesgo de abandono **15 veces mayor** que los contratos de **2 años**.

- **Alerta tecnológica:**  
  El servicio de **fibra óptica** presenta el **coeficiente positivo de riesgo más alto (1.01)**, lo que sugiere posible insatisfacción en este segmento.

---

## 🎯 Conclusiones Estratégicas

- **Onboarding crítico:**  
  Implementar seguimiento intensivo durante el **primer mes de servicio**.

- **Migración de contratos:**  
  Incentivar el paso de modalidad **mensual a anual** para aumentar la retención.

- **Revisión del servicio de fibra óptica:**  
  Investigar posibles **problemas técnicos o desajustes de precio**.

- **Métricas de negocio:**  
  Priorizar **Recall sobre Accuracy** para minimizar la pérdida de clientes en riesgo.

---

## 🎓 Autor

**Iván Marcial**

Proyecto desarrollado para el programa **Oracle Next Education (ONE)** en alianza con **Alura Latam**.
