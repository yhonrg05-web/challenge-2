# 🏥 Challenge 2: Pipeline de Machine Learning - Salud Pública

**Caso Asignado (Tipo B):** Infecciones Respiratorias Agudas (IRA) y Neumonía en Menores de 5 Años en el Perú.

---

## 📌 1. Presentación del Caso y Problema

### **Objetivo**
Definir y abordar la crisis de salud pública generada por las Infecciones Respiratorias Agudas (IRA) mediante la implementación de un flujo de aprendizaje (Pipeline) basado en Inteligencia Artificial.

### **Definición del Problema**
En el Perú, las Infecciones Respiratorias Agudas (IRA) y la neumonía son una de las principales causas de mortalidad en niños menores de 5 años. Durante las épocas de friaje y bajas temperaturas, el sistema de salud enfrenta:
* **Saturación crítica** de los centros médicos y hospitales.
* **Escasez de recursos vitales** (camas UCI pediátricas, oxígeno y personal médico).
* **Tiempos de respuesta lentos** ante pacientes críticos que requieren traslados o derivaciones inmediatas.

### **Justificación del uso de Inteligencia Artificial (IA) y Machine Learning (ML)**
Abordar esta problemática con IA es fundamental porque los métodos de triaje y asignación manual colapsan y no escalan durante las emergencias sanitarias. El uso de Machine Learning permite:
1. **Automatizar el Razonamiento y la Búsqueda:** Algoritmos de búsqueda informada (como A*) pueden derivar pacientes al hospital óptimo evaluando en tiempo real la disponibilidad de camas y minimizando la distancia geográfica.
2. **Predecir la Demanda de Recursos:** Modelos predictivos (como la **Regresión Lineal**) pueden estimar los días de estancia hospitalaria de un paciente basándose en sus signos vitales (ej. saturación de oxígeno), permitiendo anticipar cuándo se liberarán camas críticas.
3. **Optimizar Decisiones:** Pasar de un enfoque reactivo a uno predictivo, salvando vidas mediante la reducción de tiempos de espera.

---

## 🗺️ 2. Representación del Espacio de Estados

### **Objetivo**
Representar formalmente el proceso de atención y derivación de un paciente pediátrico crítico dentro de la red de salud para su posterior modelado computacional.

### **Modelo Conceptual**
* **📍 Estado Inicial:** 
  Ingreso de un paciente pediátrico (menor de 5 años) con dificultad respiratoria aguda a la red de salud.
* **⚙️ Operadores (Transiciones):**
  * `Evaluar_Triaje(paciente)`: Clasifica el nivel de riesgo clínico (Leve, Moderado, Crítico).
  * `Derivar_Emergencia(paciente, hospital)`: Traslada al paciente al centro de salud más adecuado.
  * `Asignar_Cama_UCI(hospital)`: Otorga soporte vital si existe el recurso.
  * `Asignar_Hospitalizacion(hospital)`: Otorga una cama regular para observación médica.
* **⚠️ Restricciones:**
  * **Recursos Limitados:** Capacidad operativa máxima por centro ($camas\_disponibles \ge 1$).
  * **Costo de Tiempo:** Distancia geográfica máxima permitida para un traslado seguro (prioridad de minimizar kilómetros de recorrido).
* **🎯 Estado Objetivo:** 
  Paciente estabilizado, con cama clínica asignada e iniciando tratamiento oportuno.

### **Representación Visual (Diagrama de Transición de Estados)**
```text
[ ESTADO INICIAL: Paciente Menor de 5 años con IRA ]
                              │
                              ▼
                     [ EVALUACIÓN TRIAJE ]
                    /                     \
         (Saturación > 95%)          (Saturación < 90%)
                /                             \
               ▼                               ▼
        [ CASO LEVE ]                   [ CASO CRÍTICO ]
               │                               │
        [ Consulta ]                    [ Emergencia ]
               │                               │
        [ Alta Médica ]                 [ Asignación ]
                                       /              \
                                      ▼                ▼
                        [ Cama Hospitalización ]  [ Cama UCI ]
                                      \                /
                                       ▼              ▼
                                 [ ESTADO OBJETIVO ]
                              (Paciente Estabilizado)
