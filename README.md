# Competencia Kaggle: Predicción de Personalidad Introvertido vs. Extrovertido

Este repositorio contiene la solución para la competencia de Kaggle **"Predict the Introverts from the Extroverts"**. El objetivo del proyecto fue desarrollar un modelo de machine learning capaz de clasificar la personalidad de un individuo como introvertida o extrovertida basándose en las respuestas de un cuestionario.

A través de un proceso sistemático de análisis, preprocesamiento avanzado, optimización de modelos y ensamblado, se logró un **Top Score de 0.9757** en la tabla de clasificación de Kaggle.

## Dataset
El conjunto de datos fue proporcionado por la competencia en Kaggle y se divide en un set de entrenamiento y uno de prueba.
* **Fuente:** [Predict the Introverts from the Extroverts Kaggle Competition](https://www.kaggle.com/competitions/playground-series-s5e7)
* **Características Principales:** Incluyen respuestas numéricas y categóricas a preguntas como `Time_spent_Alone`, `Stage_fear`, `Going_outside`, y `Friends_circle_size`.
* **Variable Objetivo:** `Personality` (Clasificación binaria: 'Introvert' o 'Extrovert').

## Flujo de Trabajo y Metodología
El proyecto se estructuró en dos fases principales, documentadas en dos notebooks separados, para demostrar un enfoque desde lo fundamental hasta lo avanzado.

#### 1. Análisis Exploratorio de Datos (EDA)
Se realizó un análisis exhaustivo para entender la naturaleza de los datos. Los hallazgos clave incluyeron:
* Fuertes correlaciones entre varias características y la variable objetivo.
* Un **desbalance de clases** significativo, con una mayor proporción de extrovertidos.

#### 2. Preprocesamiento de Datos
Se exploraron dos estrategias de imputación para manejar los valores nulos:
* **Notebook 1 (Base):** Se utilizó la **imputación por la mediana**, un método robusto y computacionalmente eficiente.
* **Notebook 2 (Avanzado):** Se implementó el **`IterativeImputer`** de Scikit-learn, un método multivariado que estima cada valor faltante basándose en las demás características para lograr una imputación más precisa.

#### 3. Modelado y Selección
Se evaluó el rendimiento de varios algoritmos de clasificación potentes:
* `RandomForestClassifier`
* `XGBoost`
* `LightGBM`

El **`RandomForestClassifier`** demostró consistentemente ser el modelo individual más fuerte en este problema.

#### 4. Optimización de Hiperparámetros
Para maximizar el rendimiento, se utilizaron dos técnicas de optimización:
* **`GridSearchCV`:** Para una búsqueda exhaustiva en un espacio de parámetros definido.
* **`Optuna`:** Para una búsqueda más inteligente y eficiente utilizando optimización bayesiana.

#### 5. Ensamble de Modelos
Se experimentó con técnicas de ensamblado para buscar una mejora final:
* **`VotingClassifier`:** Combinando las predicciones de los mejores modelos.
* **`StackingClassifier`:** Implementando un meta-modelo para aprender a combinar las predicciones de forma óptima.

Curiosamente, se descubrió que el **modelo `RandomForestClassifier` individual, una vez optimizado, superaba a los ensambles**, demostrando su robustez y adecuación para este dataset.

## Resultados
El proceso de experimentación y optimización culminó en un modelo de alto rendimiento.

* **Modelo Campeón 🏆:** `RandomForestClassifier`
* **Método de Preprocesamiento:** Imputación de nulos con **`IterativeImputer`**.
* **Mejores Hiperparámetros:**
    * `max_depth`: 20
    * `min_samples_leaf`: 2
    * `n_estimators`: 200
* **Score Final en Kaggle:** **0.975708**

## Conclusión
Este proyecto demuestra un flujo de trabajo completo de machine learning, desde el análisis inicial hasta la optimización avanzada. La conclusión clave es doble:
1.  Las técnicas de preprocesamiento avanzado como **`IterativeImputer`** pueden ofrecer mejoras significativas sobre métodos más simples.
2.  Un **modelo individual robusto y bien optimizado** (`RandomForestClassifier` en este caso) a veces puede ser superior a ensambles más complejos, destacando la importancia de la selección y ajuste del modelo.

El resultado final valida la efectividad de un enfoque metódico y experimental para resolver problemas de clasificación.
