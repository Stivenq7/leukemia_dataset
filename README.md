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
