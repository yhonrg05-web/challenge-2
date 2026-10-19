# 📂 Directorio de Datos: Morbilidad Infantil (MINSA)

Este directorio almacena los conjuntos de datos oficiales procesados y utilizados para el análisis epidemiológico y los modelos de Inteligencia Artificial Predictiva del proyecto (**Challenge 2 - UPCH**).

---

## 📋 Información del Dataset

* **Fuente Oficial:** Ministerio de Salud del Perú (MINSA) - Estadísticas de Morbilidad.
* **Año de Referencia:** 2009.
* **Dominio Clínico:** Pediatría (Enfoque en Infecciones Respiratorias Agudas - IRA y Neumonía en menores de 12 años).
* **Formato:** Archivo estructurado de valores separados por comas (`.csv`).

---

## 📑 Estructura de Columnas del Archivo `morbilidad_ira_pediatrica_2009.csv`

El dataset contiene los registros agrupados por patologías según la clasificación CIE-10 y su distribución por grupos etarios:

| Columna | Descripción del Campo |
| :--- | :--- |
| **`GRUPO`** | Grupo de diagnóstico clínico y código CIE-10 asociado (Ej. `(J09 - J18) INFLUENZA Y NEUMONIA`). |
| **`00a - 11a`** | Volumen de casos registrados en población infantil de 0 a 11 años (Población objetivo principal). |
| **`12a - 17a`** | Casos registrados en adolescentes. |
| **`18a - 29a`** | Casos registrados en adultos jóvenes. |
| **`30a - 59a`** | Casos registrados en adultos. |
| **`60a >`** | Casos registrados en adultos mayores. |
| **`TOTAL`** | Sumatoria total de morbilidad registrada para la patología a nivel nacional. |

---

## 🔍 Uso y Procesamiento en los Notebooks

Los datos contenidos en este archivo son consumidos de forma remota y automatizada (vía enlace RAW de GitHub) por los scripts de Python en los notebooks:
1. **`01_busqueda_optimizacion.ipynb`**: Exploración, validación de esquemas y metadatos de la fuente.
2. **`02_regresion_prediccion.ipynb`**: Filtrado de patologías respiratorias (CIE-10: `J00 - J99`), limpieza de formatos numéricos y alimentación del algoritmo de Regresión Lineal.
