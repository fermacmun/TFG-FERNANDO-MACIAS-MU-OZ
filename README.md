# TFG-FERNANDO-MACIAS-MUNOZ
## 🧬 Análisis de Expresión Génica para la Detección de Cáncer de Mama y Útero

Este proyecto tiene como objetivo aplicar modelos de aprendizaje automático sobre datos de expresión génica para clasificar tejidos normales y tumorales en cáncer de mama y útero, y explorar los genes más relevantes implicados en cada condición.

---

📁 **Estructura del Proyecto**

```text
TFG CODIGO/
│
├── MEZCLA DE CODIGOS.ipynb         # Notebook principal con todo el flujo
├── data/                           # Datos de expresión génica y genes relevantes
│   ├── brca-rsem-fpkm-tcga.txt         # Mama sano
│   ├── brca-rsem-fpkm-tcga-t.txt       # Mama tumoral
│   ├── ucec-rsem-fpkm-tcga.txt         # Útero sano
│   ├── ucec-rsem-fpkm-tcga-t.txt       # Útero tumoral
│   └── tsgoncogene.xlsx                # Genes asociados al cáncer

```
---
## 🧪 Flujo del Proyecto (Paso a Paso)

Este proyecto sigue un flujo estructurado de análisis de datos de expresión génica para detectar y clasificar muestras tumorales y normales, específicamente en **tejido mamario** y **uterino**.

---

### 1. 📥 Carga y Exploración de Datos

- Se cargan archivos de expresión génica (FPKM) para tejidos normales y tumorales de mama y útero.
- Se importa una lista de genes relevantes (oncogenes y genes supresores de tumores) desde un archivo Excel.

---

### 2. 🧬 Filtrado de Genes Relevantes

- Se filtran los datos de expresión para conservar solo los genes presentes en la lista proporcionada (`tsgoncogene.xlsx`).
- Se manejan duplicados priorizando coincidencias con el símbolo génico (`Hugo_Symbol`).

---

### 3. ✂️ División en Conjuntos de Entrenamiento y Prueba

- Los datos se dividen manteniendo las dos primeras columnas (identificadores).
- La división se aplica individualmente a cada subconjunto (mama y útero, normal y tumor).

---

### 4. 🧱 Construcción de Matrices de Muestras

- Se aseguran genes comunes entre tejidos.
- Se combinan las muestras tumorales y normales por separado y luego se unifican en un `train_set` y un `test_set`.
- Se agregan etiquetas de clase (`Normal`, `Tumor`) y de tejido (`Mama`, `Útero`).

---

### 5. ⚙️ Preprocesamiento

- Se aplica la transformación **Yeo-Johnson** para reducir la asimetría en la distribución de los genes.
- Se realiza un escalado estándar (z-score).
- Se eliminan genes con **varianza casi nula**.
- Se reduce la dimensionalidad con **PCA**, conservando el 95% de la varianza.

---

### 6. 🧠 Entrenamiento y Evaluación de Modelos

Se evalúan múltiples clasificadores utilizando validación cruzada y prueba final:

- `Logistic Regression`
- `Random Forest`
- `SVM`
- `k-NN`
- `XGBoost`
- `LDA`
- `Árbol de Decisión (CART)`
- `MLP (Red Neuronal)`

Cada uno se entrena con los datos reducidos por PCA.

---

### 7. 🧪 Comparación de Modelos

- Se grafican las métricas: Accuracy (entrenamiento y test) y F1-score.
- Se identifican los 3 mejores modelos basados en rendimiento global.

---

### 8. 🔍 Análisis de Importancia de Genes

- Se usa **permutation importance** para calcular la importancia de los genes en los 3 modelos top (`Logistic`, `SVM`, `MLP`).
- Se identifican genes comunes más relevantes.
- Se visualiza con diagramas de barras y de Venn.

---

### 9. 🧬 Análisis Individual por Tejido

Se repite el proceso de análisis, pero por separado:

- **Cáncer de Mama**
  - Entrenamiento de modelos ligeros
  - Permutation importance
  - Visualización de genes más relevantes

- **Cáncer de Útero**
  - Análisis independiente similar al de mama

---

### 10. 📊 Explicabilidad con DALEX

- Se entrena `Logistic`, `SVM`, y `MLP` usando nombres reales de genes.
- Se visualiza la importancia de variables con DALEX.
- Se generan gráficos de tipo SHAP y perfiles individuales de variables clave.

---


