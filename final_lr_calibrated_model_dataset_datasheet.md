
## Datasheet del Conjunto de Datos `diabetes.csv`

Este datasheet proporciona una descripción detallada del conjunto de datos `diabetes.csv` utilizado en este análisis, recopilando información clave obtenida durante la exploración y preprocesamiento de los datos.

### 1. Origen y Curadores
- **Origen:** El conjunto de datos `diabetes.csv` es un subconjunto del National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK). Es un dataset clásico conocido como 'Pima Indian Diabetes Dataset', utilizado comúnmente para problemas de predicción de diabetes.
- **Método de Recolección de Datos:** Las mediciones diagnósticas fueron tomadas de pacientes femeninas de ascendencia Pima India, mayores de 21 años. El período exacto de recolección de datos no se especifica en el contexto actual.

### 2. Contenido del Conjunto de Datos
- **Características (Variables):** El dataset contiene 9 variables:
  - `Pregnancies`: Número de veces embarazada. (`int64`)
  - `Glucose`: Concentración de glucosa en plasma a las 2 horas en una prueba oral de tolerancia a la glucosa. (`float64`)
  - `BloodPressure`: Presión arterial diastólica (mm Hg). (`float64`)
  - `SkinThickness`: Espesor del pliegue cutáneo del tríceps (mm). (`float64`)
  - `Insulin`: Insulina sérica de 2 horas (mu U/ml). (`float64`)
  - `BMI`: Índice de masa corporal (peso en kg / (altura en m)^2). (`float64`)
  - `DiabetesPedigreeFunction`: Función de pedigrí de la diabetes (una función que pondera la probabilidad de diabetes basada en el historial familiar). (`float64`)
  - `Age`: Edad (años). (`int64`)
  - `Outcome`: Variable objetivo, clase (0 si no tiene diabetes, 1 si tiene diabetes). (`int64`)

- **Dimensiones del Dataset:**
  - Número de filas (muestras): 768
  - Número de columnas (características): 9

### 3. Preprocesamiento y Calidad de Datos
- **Valores Faltantes (Explícitos):** No se encontraron valores `NaN` explícitos inicialmente.
- **Valores Faltantes (Identificados):** Se identificaron valores de `0` en las columnas `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin` y `BMI` como imposibilidades fisiológicas y fueron reemplazados por `np.nan`. El recuento de `NaN`s después de esta operación es:
  - `Glucose`: 5 `NaN`s
  - `BloodPressure`: 35 `NaN`s
  - `SkinThickness`: 227 `NaN`s
  - `Insulin`: 374 `NaN`s
  - `BMI`: 11 `NaN`s
- **Filas Duplicadas:** No se encontraron filas duplicadas en el dataset.
- **Balance de Clases de la Variable Objetivo (`Outcome`):**
  - 'No diabetes' (0): Aproximadamente 65.1%
  - 'Diabetes' (1): Aproximadamente 34.9%
  Esto indica un desequilibrio de clases, lo cual fue abordado mediante técnicas de balanceo de clases como SMOTE en etapas posteriores del modelado.
- **Pasos Iniciales de Preprocesamiento:**
  1. Identificación y reemplazo de valores `0` fisiológicamente imposibles con `np.nan`.
  2. Imputación de estos `np.nan`s utilizando estrategias como KNNImputer, seleccionada como la mejor opción en una etapa de análisis de imputación.

### 4. Consideraciones Éticas y Uso Responsable
- **Sesgos:** El dataset Pima Indian Diabetes podría tener sesgos inherentes relacionados con el grupo étnico y el género, lo que podría llevar a un rendimiento diferencial del modelo en subgrupos poblacionales no representados. Es crucial monitorear su desempeño en diversas poblaciones.
- **Equidad y transparencia:** Se ha priorizado la explicabilidad mediante SHAP para comprender las influencias de las características en las predicciones individuales. Sin embargo, se debe ser consciente de que los modelos predictivos no están exentos de sesgos incluso con estas herramientas.
- **Uso Previsto:** El modelo desarrollado con este dataset está diseñado para asistir a profesionales de la salud en la identificación temprana de individuos con riesgo de diabetes, no como una herramienta de diagnóstico definitivo. Las predicciones deben ser interpretadas en un contexto clínico más amplio y no deben reemplazar el juicio médico experto.
- **Mal uso / Riesgos:** Un uso inadecuado o la confianza excesiva en las predicciones del modelo sin supervisión médica podría llevar a diagnósticos erróneos, ansiedad innecesaria en los pacientes o falta de seguimiento adecuado.

