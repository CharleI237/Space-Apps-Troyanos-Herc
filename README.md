# 🌌 EXOPLANET AI CLASSIFIER

### NASA Space Apps Challenge 2025 – "A World Away: Hunting for Exoplanets with AI"

---

## 🧬 Descripción del Proyecto

**Exoplanet AI Classifier** es un sistema de inteligencia artificial diseñado para **clasificar exoplanetas** en diferentes categorías según su probabilidad de ser reales, falsos positivos o candidatos confirmados.  
El proyecto fue desarrollado para el reto **“A World Away: Hunting for Exoplanets with AI”** durante el **NASA Space Apps Challenge 2025**.

El sistema entrena y evalúa modelos de *machine learning* sobre datos del **NASA Exoplanet Archive**, incluyendo tres conjuntos principales:

* **Kepler Exoplanet Archive** → Modelo XGBoost (Kepler XGB)
* **K2 Exoplanet Archive** → Modelo Random Forest (RFCFS)
* **TOI (TESS Object of Interest)** → Modelo XGBoost (versión estable)

Cada modelo fue desarrollado con un enfoque en **limpieza de datos, eliminación de fugas y equilibrio entre precisión y generalización**.

---

## 🚀 Modelos Desarrollados

### ☀️ 1. EXO-KEPLER XGB Model  
**(XGBoost – Kepler Dataset)**  

* **Descripción:**  
Modelo de clasificación supervisada desarrollado a partir de los datos del **Kepler Exoplanet Archive (NASA)**, con el objetivo de identificar y clasificar candidatos a exoplanetas en tres categorías principales.  
El modelo fue entrenado utilizando el algoritmo **XGBoost**, priorizando la precisión y estabilidad sin sobreajuste, manteniendo un pipeline limpio y reproducible.  

* **Algoritmo:** XGBoost  
* **Dataset:** 8,776 registros originales → 1,073 muestras de prueba  
* **Accuracy:** 0.904  
* **Clases:**  
  * 0 – False Positive  
  * 1 – Candidate  
  * 2 – Confirmed  

#### 🔹 Métricas:

| Clase               | Precisión | Recall | F1-Score | Soporte |
| :------------------ | :-------: | :----: | :------: | :-----: |
| False Positive (0)  |    0.85   |  0.83  |   0.84   |   326   |
| Candidate (1)       |    0.87   |  0.89  |   0.88   |   389   |
| Confirmed (2)       |    0.99   |  0.99  |   0.99   |   358   |
| **Accuracy Global** | **0.904** |        |          |  1,073  |

---

### 🪐 2. EXO-K2 RFCFS Model  
**(Random Forest Clean Feature Set)**  

* **Descripción:**  
Modelo de clasificación basado en 17 variables orbitales y estelares derivadas del *K2 Exoplanet Archive (NASA)*.  
Entrenado con el algoritmo **Random Forest (200 árboles)**, priorizando interpretabilidad y estabilidad, sobre un dataset cuidadosamente depurado para eliminar duplicados y valores inconsistentes.  

* **Algoritmo:** Random Forest  
* **Dataset:** 1,806 registros únicos, 17 características limpias  
* **Accuracy:** 0.801  
* **Clases:**  
  * CANDIDATE  
  * CONFIRMED  
  * FALSE POSITIVE  
  * REFUTED  

#### 🔹 Métricas:

| Clase               | Precisión | Recall | F1-Score | Soporte |
| :------------------ | :-------: | :----: | :------: | :-----: |
| CANDIDATE           |    0.78   |  0.89  |   0.83   |   196   |
| CONFIRMED           |    0.83   |  0.72  |   0.77   |   116   |
| FALSE POSITIVE      |    0.84   |  0.65  |   0.73   |    48   |
| REFUTED             |    0.00   |  0.00  |   0.00   |    2    |
| **Accuracy Global** | **0.801** |        |          |   362   |

---

### 🌠 3. EXO-TOI XGBStable Model  
**(XGBoost Stable Version, TOI Dataset)**  

* **Descripción:**  
Modelo de clasificación multi-etiqueta entrenado sobre el conjunto **TESS Object of Interest (TOI)**.  
El algoritmo **XGBoost** fue ajustado con hiperparámetros que equilibran precisión y generalización, evitando sobreajuste y fugas de información.  

* **Algoritmo:** XGBoost  
* **Dataset:** 7,703 registros – 27 variables (sin fugas, normalizadas)  
* **Accuracy:** 0.746  
* **Clases:**  
  * APC (Ambiguous Planet Candidate)  
  * CP (Confirmed Planet)  
  * FA (False Alarm)  
  * FP (False Positive)  
  * KP (Known Planet)  
  * PC (Planet Candidate)  

#### 🔹 Métricas:

| Clase               | Precisión | Recall | F1-Score | Soporte |
| :------------------ | :-------: | :----: | :------: | :-----: |
| APC                 |    0.47   |  0.20  |   0.28   |    92   |
| CP                  |    0.68   |  0.51  |   0.58   |   137   |
| FA                  |    0.20   |  0.05  |   0.08   |    20   |
| FP                  |    0.63   |  0.51  |   0.56   |   239   |
| KP                  |    0.84   |  0.62  |   0.71   |   117   |
| PC                  |    0.78   |  0.93  |   0.85   |   936   |
| **Accuracy Global** | **0.746** |        |          |   1541  |

---

## 🧽 Requisitos

Para ejecutar el proyecto localmente:

```bash
git clone https://github.com/CharleI237/Space-Apps-Troyanos-Herc/
cd exoplanet-ai-classifier
pip install -r requirements.txt
