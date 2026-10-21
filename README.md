Proyecto Leucemia: Pipeline ML & Estado Actual
1. Repositorio & Archivos
• Repositorio GitHub: Stivenq7/leukemia_dataset (rama main)

• Archivo dataset: biased_leukemia_dataset.csv

• Archivo de utilidades: funciones.py (del repositorio base del curso)

2. Decisiones de Limpieza y Preprocesamiento
• Tipo de problema: Clasificación binaria (Leukemia_Status: Positive=1, Negative=0).

• Desbalance de clases: ~14.9% positivos vs ~85.1% negativos.

• Variables eliminadas: Patient_ID y variables sociodemográficas/geográficas (Country, Ethnicity, Socioeconomic_Status, Urban_Rural, Gender) para mitigar sesgo algorítmico y ruido.

3. Próximos Pasos (Flujo de Modelado para Mañana)
1. Binarización de variables clínicas de tipo Yes/No y del target.

2. Split estratificado (80/20) con stratify=y.

3. Escalado numérico con StandardScaler sobre variables continuas.

4. Modelado con class_weight='balanced' (Logistic Regression, Random Forest).

5. Evaluación focalizada en Recall, F1-Score, PR-AUC y ROC-AUC.

6. Análisis de Importancia de Características (Feature Importance).

7. https://www.kaggle.com/code/mrinalbasakshuvo/leukemia/notebook



El flujo de trabajo toma los datos crudos y los transforma en un sistema de apoyo a la decisión médica. No busca emitir un simple veredicto binario ("sano" vs. "enfermo"), sino cuantificar la probabilidad de riesgo de cada paciente y clasificarlo en un nivel de prioridad asistencial (Triage).

Tipos de Modelado que se van a ManejarSe emplean dos familias de algoritmos complementarias para contrastar una aproximación lineal e interpretable frente a una no lineal basada en ensambles:1. Regresión Logística (LogisticRegression)Qué es: Un modelo paramétrico lineal que estima la probabilidad del evento $P(Y=1\vert{}X)$ mediante la función sigmoide:$$P(Y=1\vert{}X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 X_1 + \dots + \beta_p X_p)}}$$Por qué se utiliza: Es el estándar en bioestadística y medicina. Permite interpretar de manera directa los coeficientes ($\beta$) en términos de odds ratios (razón de momios). Si una variable aumenta, se conoce con precisión matemática cuánto se incrementa o reduce el riesgo.Requisito técnico: Es muy sensible a la escala de las variables, por lo que exige escalado numérico previo (StandardScaler).


Random Forest Classifier (RandomForestClassifier)
Qué es: Un algoritmo de ensamble no paramétrico basado en Bagging (Bootstrap Aggregating) que construye múltiples árboles de decisión descorrelacionados y promedia sus predicciones.

Por qué se utiliza: Captura interacciones biológicas complejas y relaciones no lineales entre factores clínicos (por ejemplo, el efecto conjunto de blastos elevados, edad avanzada y mutación genética presente).

Requisito técnico: Es invariante a transformaciones monotónicas; no requiere escalado numérico y es resistente a valores atípicos (outliers).


