# Challenge 1: Pipeline de Machine Learning - Salud Pública (IRA)

## 1. Presentación del Caso y Problema
**Problema:**
En el Perú, las Infecciones Respiratorias Agudas (IRA) y la neumonía representan una de las principales causas de morbilidad y mortalidad en niños menores de 5 años. Durante las temporadas de bajas temperaturas (friajes y heladas), los centros de salud experimentan una saturación crítica, lo que dificulta la atención oportuna y la asignación eficiente de recursos como camas de hospitalización y camas UCI pediátricas.

**Justificación del uso de Inteligencia Artificial y Machine Learning:**
Abordar esta problemática con métodos tradicionales resulta ineficiente debido a la variabilidad clínica y la velocidad a la que evolucionan los cuadros respiratorios. La Inteligencia Artificial y el Machine Learning permiten:
1. **Razonamiento y Búsqueda:** Automatizar la búsqueda de la mejor alternativa hospitalaria (menor distancia y mayor disponibilidad) mediante algoritmos heurísticos cuando el tiempo es crítico.
2. **Predicción (Regresión):** Estimar con precisión el tiempo de estancia hospitalaria de un paciente en función de sus signos vitales (ej. saturación de oxígeno), optimizando la gestión de camas y la rotación hospitalaria.

---

## 2. Representación del Espacio de Estados

Para la gestión de un paciente crítico, el problema se modela formalmente de la siguiente manera:

* **Estado Inicial:** Ingreso de un paciente pediátrico (menor de 5 años) con dificultad respiratoria aguda a la red de salud.
* **Operadores (Transiciones):**
  * `Evaluar_Triaje()`: Determina la gravedad clínica del paciente.
  * `Derivar_Emergencia()`: Traslado inmediato si la saturación de oxígeno es baja.
  * `Asignar_Cama_UCI()` / `Asignar_Hospitalización()`: Asignación de recursos según disponibilidad.
* **Restricciones:** 
  * Capacidad máxima de camas por centro de salud.
  * Distancia geográfica máxima permitida para un traslado seguro (costo de tiempo).
* **Estado Objetivo:** Paciente estabilizado con cama clínica asignada e iniciando tratamiento oportuno.

**Representación Visual:**
