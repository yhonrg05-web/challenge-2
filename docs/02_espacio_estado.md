# 🗺️ Representación del Espacio de Estados

## 1. Modelo Conceptual
El proceso de atención y derivación de un paciente pediátrico crítico dentro de la red de salud se modela de la siguiente manera:

* **📍 Estado Inicial:** Ingreso de un paciente pediátrico (menor de 5 años) con dificultad respiratoria aguda a la red de salud.
* **⚙️ Operadores (Transiciones):**
  * `Evaluar_Triaje(paciente)`: Clasifica el nivel de riesgo clínico (Leve, Moderado, Crítico).
  * `Derivar_Emergencia(paciente, hospital)`: Traslada al paciente al centro de salud más adecuado.
  * `Asignar_Cama_UCI(hospital)`: Otorga soporte vital de alta prioridad.
  * `Asignar_Hospitalizacion(hospital)`: Otorga una cama regular para observación.
* **⚠️ Restricciones:**
  * **Recursos Limitados:** Capacidad operativa máxima por centro ($camas\_disponibles \ge 1$).
  * **Costo de Traslado (Tiempo/Distancia):** Prioridad de minimizar kilómetros de recorrido para evitar complicaciones durante el traslado.
* **🎯 Estado Objetivo:** Paciente estabilizado, con cama clínica asignada e iniciando tratamiento oportuno.

## 2. Representación Visual (Diagrama de Estados)
```text
[ ESTADO INICIAL: Paciente con IRA ]
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
