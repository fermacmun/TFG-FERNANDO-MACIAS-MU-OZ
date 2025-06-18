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

---

## 🔧 Requisitos

Para ejecutar correctamente este proyecto, necesitas tener instalado **Python 3.8 o superior** y las siguientes librerías:

### Instalación rápida

Puedes instalar todas las dependencias ejecutando:

```bash
pip install -r requirements.txt
