# Validación técnica de las soluciones ExpoClean

## 1. ¿Qué se está validando?

La validación de ExpoClean no consiste únicamente en demostrar que existen productos o investigaciones similares. Se deben validar tres aspectos:

1. **Viabilidad técnica:** las etapas y componentes propuestos pueden funcionar como sistema.
2. **Desempeño medible:** el prototipo entrega una dosis controlada y reduce la turbidez del agua de entrada.
3. **Relevancia ambiental:** el control de la dosificación y el pretratamiento pueden reducir desperdicios y mejorar la gestión del agua residual.

Por eso, las fuentes externas se utilizan como **referencia o línea base**, mientras que los resultados del prototipo deben obtenerse mediante pruebas propias.

---

## 2. Validación de la Solución 2: estación inteligente de dosificación

### 2.1 Referencia comercial: SmartDose™

SmartDose™, de Diversey/Solenis, es una referencia comercial que demuestra que la dosificación controlada de productos concentrados es una solución técnicamente viable en limpieza profesional. Según la página oficial del producto, SmartDose es un sistema portátil que entrega dosis precisas de concentrado, utiliza dos tamaños de dosificación y está diseñado para llenar botellas, cubetas, fregadoras automáticas y fregaderos. También indica que no requiere conexión de agua y que busca evitar la sobredosificación y la subdosificación.

Fuente oficial: [SmartDose™ — Solenis/Diversey](https://www.solenis.com/es-mx/products-and-services/commercial-cleaning/dilution-control/smartdose/).

### 2.2 ¿Qué valida SmartDose para ExpoClean?

SmartDose permite validar la **hipótesis tecnológica** de ExpoClean:

> Si un sistema entrega una cantidad definida de producto en lugar de depender de la estimación visual del operario, es posible estandarizar la preparación de soluciones de limpieza y reducir el riesgo de sobredosificación.

SmartDose valida el principio de dosificación controlada, pero no valida directamente los resultados de ExpoClean. Nuestro prototipo utiliza otra arquitectura: una aplicación web envía una orden al ESP32, el ESP32 activa un relé y la bomba de 12 V dispensa el producto durante un tiempo calculado a partir de su caudal calibrado.

### 2.3 Comparación con el prototipo ExpoClean

| Aspecto | SmartDose | ExpoClean |
|---|---|---|
| Tipo de control | Bomba mecánica integrada en una botella. | Bomba eléctrica de 12 V controlada por ESP32. |
| Selección | Selector mecánico con dosis predefinidas. | Aplicación web, QR y volumen solicitado. |
| Medición inicial | Dosis volumétrica del sistema comercial. | Tiempo de activación basado en caudal calibrado. |
| Registro digital | La página consultada no presenta un historial por usuario o jornada. | Registra la orden y el consumo estimado en la aplicación. |
| Escalabilidad | Sistema asociado a su formato y productos. | Puede ampliarse con más bidones, bombas, sensores y productos compatibles. |
| Validación de ExpoClean | Sirve como referencia de mercado. | Debe comprobarse mediante medición directa del volumen dispensado. |

La diferenciación de ExpoClean no consiste en afirmar que inventa la dosificación automática. Consiste en adaptar el principio a una estación conectada, modular y trazable, que puede relacionarse con la operación de limpieza y con la gestión posterior del agua gris.

### 2.4 Prueba experimental de dosificación

#### Objetivo

Determinar si la estación entrega un volumen cercano al solicitado y si la aplicación registra correctamente el ciclo.

#### Procedimiento

1. Medir el caudal de la bomba con agua o con un líquido seguro para pruebas.
2. Realizar al menos cinco mediciones con el mismo tiempo de activación.
3. Calcular el caudal promedio en mL/s.
4. Programar volúmenes conocidos, por ejemplo 10, 20 y 50 mL.
5. Recoger cada dosis en una probeta o pesarla en una balanza.
6. Comparar el volumen solicitado con el volumen medido.
7. Repetir la prueba con diferentes niveles del bidón para observar si cambia el caudal.
8. Verificar que el ESP32 detenga la bomba y que la aplicación registre el ciclo.

#### Indicadores

```text
Caudal (mL/s) = volumen medido (mL) / tiempo de activación (s)

Error absoluto (mL) = |volumen medido - volumen solicitado|

Error relativo (%) =
error absoluto / volumen solicitado × 100

Exactitud (%) =
volumen medido / volumen solicitado × 100
```

#### Tabla para registrar resultados

| Prueba | Volumen solicitado (mL) | Tiempo (s) | Volumen medido (mL) | Error (mL) | Error (%) | Registro correcto |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 10 |  |  |  |  | Sí / No |
| 2 | 20 |  |  |  |  | Sí / No |
| 3 | 50 |  |  |  |  | Sí / No |
| 4 | 20 |  |  |  |  | Sí / No |
| 5 | 50 |  |  |  |  | Sí / No |

#### Criterio de aceptación sugerido

Para una demostración inicial, se puede considerar que el sistema es funcional si completa correctamente el ciclo de encendido, bombeo, apagado y registro, y si el error de volumen se mantiene dentro del margen definido por el equipo. El margen final debe establecerse después de conocer la precisión real de la bomba; no debe declararse un porcentaje de ahorro o exactitud sin haberlo medido.

---

## 3. Validación de la Solución 1: filtración y pretratamiento de aguas grises

### 3.1 Fundamento científico de la arquitectura

La Solución 1 utiliza una secuencia de prefiltrado, sedimentación, filtración con grava y arena, carbón activado, bombeo y monitoreo de turbidez. Esta configuración está respaldada por investigaciones que han estudiado sistemas de tratamiento de aguas grises con medios granulares.

Las investigaciones no garantizan que el prototipo ExpoClean alcance los mismos resultados. Las condiciones dependen del tipo de agua, tamaño y profundidad de los medios, tiempo de retención hidráulica, caudal, saturación y mantenimiento del filtro. Por eso, sus porcentajes se utilizan como **referencias de desempeño**, no como resultados propios.

### 3.2 Fuentes de referencia

| Fuente | Relación con ExpoClean | Resultado reportado | Uso en la validación |
|---|---|---|---|
| [Zipf, Siebert, Pinheiro y Conegero (2016)](https://pubmed.ncbi.nlm.nih.gov/27045540/), *Simplified greywater treatment systems* | Utiliza filtración lenta con arena y carbón activado granular. | Reporta una reducción promedio de turbidez de aproximadamente 61% con el filtro de arena; también analiza color, DQO, DBO, surfactantes y coliformes. | Fundamenta el uso de arena y carbón activado y sirve como referencia conservadora para la turbidez. |
| [Ali, Ali y Jaafar (2020)](https://doi.org/10.31026/j.eng.2020.10.05), *Chemical-Free Greywater Treatment* | Integra prefiltrado, aireación, sedimentación y carbón activado con arena. | Reporta 94% de reducción de turbidez, 93% de DQO y 91% de aceites bajo las condiciones estudiadas. | Sustenta que la combinación de sedimentación y carbón activado puede superar a una filtración simple; no debe trasladarse directamente al prototipo. |
| [Tusiime et al. (2022)](https://doi.org/10.1016/j.envc.2022.100641), *Performance of lab-scale filtration system* | Compara columnas de grava + arena y grava + arena + carbón activado granular. | Reporta reducciones de parámetros seleccionados entre 60,8% y 100% en una columna, con influencia del tiempo de retención hidráulica y del taponamiento. | Fundamenta la selección de medios y la necesidad de medir turbidez, DBO/DQO y mantenimiento. |
| [Shaikh y Ahammed (2022)](https://pubmed.ncbi.nlm.nih.gov/36358042/), *Granular media filtration for on-site treatment of greywater* | Revisión sobre filtros granulares para tratamiento descentralizado. | Señala que el desempeño depende de la calidad del agua, el tipo y tamaño del medio, la profundidad y las condiciones de operación. | Justifica que ExpoClean debe validar su propio caudal, configuración y uso final antes de afirmar reúso. |

### 3.3 Hipótesis de validación

> Si el agua gris pasa por una malla de prefiltrado, una cámara de sedimentación y un filtro compuesto por grava, arena y carbón activado, entonces la turbidez de salida será menor que la turbidez de entrada y se retendrán residuos sólidos visibles.

La hipótesis se limita a la reducción de turbidez y sólidos. No afirma que el sistema elimine todos los contaminantes químicos o microbiológicos.

### 3.4 Prueba experimental de filtración

#### Preparación

1. Utilizar agua gris representativa de una actividad de limpieza o preparar una muestra controlada con sólidos conocidos.
2. Homogeneizar la muestra antes de tomar la medición inicial.
3. Medir el volumen total de entrada.
4. Medir la turbidez inicial con el sensor o instrumento disponible.
5. Registrar el pH y, si es posible, conductividad, sólidos suspendidos y DQO.

#### Ejecución

1. Pasar el agua por la malla de prefiltrado.
2. Dejarla reposar durante un tiempo definido en la cámara de sedimentación.
3. Retirar y pesar o fotografiar los residuos gruesos y los lodos, si es posible.
4. Bombear el agua a través de las capas de grava, arena y carbón activado.
5. Registrar el caudal y el tiempo de filtración.
6. Medir la turbidez del agua de salida.
7. Repetir la prueba al menos tres veces para observar la variabilidad.
8. Revisar si el filtro se obstruye o si la turbidez aumenta después de varios ciclos.

#### Indicadores

```text
Reducción de turbidez (%) =
(turbidez de entrada - turbidez de salida) / turbidez de entrada × 100

Remoción de sólidos (%) =
(masa de sólidos de entrada - masa de sólidos de salida) /
masa de sólidos de entrada × 100

Caudal de filtración (L/min) =
volumen filtrado / tiempo de filtración
```

#### Tabla para registrar resultados

| Prueba | Turbidez inicial | Turbidez final | Reducción (%) | Volumen procesado (L) | Tiempo (min) | Observaciones |
|---:|---:|---:|---:|---:|---:|---|
| 1 |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |

### 3.5 Interpretación de resultados

Los resultados deben interpretarse de esta manera:

- **Turbidez menor:** indica una mejora visual y física del agua, principalmente por retención de partículas.
- **Sedimentos retenidos:** demuestra que la malla y la sedimentación cumplen su función de separar sólidos.
- **Caudal decreciente:** puede indicar saturación o taponamiento del filtro.
- **Turbidez baja pero presencia de químicos:** demuestra que la claridad visual no es suficiente para declarar el agua segura.
- **Resultado variable:** indica que se deben controlar el tiempo de reposo, el caudal, la cantidad de medios filtrantes y la composición del agua.

La referencia de 61% de turbidez del estudio de 2016 puede utilizarse como una meta inicial prudente para una configuración con arena. El 94% del estudio de 2020 y los rangos del estudio de 2022 deben presentarse como resultados de otros sistemas bajo condiciones específicas, no como una promesa de ExpoClean.

---

## 4. Validación integral frente al Reto 4

| Criterio | Evidencia externa | Evidencia que debe producir ExpoClean |
|---|---|---|
| Dosificación exacta | SmartDose demuestra la viabilidad de entregar dosis controladas. | Volumen solicitado vs. volumen medido, error, repetibilidad y registro digital. |
| Reducción de químicos | La dosificación controlada evita la estimación visual. | Comparación entre método manual y estación ExpoClean en una tarea equivalente. |
| Filtración de aguas grises | Los papers respaldan sedimentación, arena y carbón activado. | Turbidez de entrada/salida, sólidos retenidos, caudal y estado del filtro. |
| Reúso | La literatura evalúa usos no potables bajo condiciones determinadas. | Análisis de calidad y decisión documentada; no asumir reúso solo por transparencia. |
| Monitoreo | Los estudios utilizan parámetros físico-químicos y operación controlada. | Historial de ciclos, lecturas del sensor, tiempos y mantenimiento. |

### Resultado mínimo demostrable

Para la presentación, el resultado mínimo defendible es:

1. demostrar que la estación dosificadora entrega un volumen programado con un error medido;
2. demostrar que el filtro retiene residuos y produce una turbidez menor que la del agua de entrada;
3. registrar los datos de ambas pruebas;
4. comparar los resultados con las referencias científicas sin atribuirles al prototipo porcentajes que todavía no se han medido;
5. explicar que el agua filtrada es para evaluación de uso no crítico y que no equivale a agua potable ni a cumplimiento automático de límites de descarga.

## 5. Conclusión de validación

Las fuentes consultadas respaldan la lógica de las dos soluciones. SmartDose demuestra que el control de dosis es una práctica viable en limpieza profesional. Los estudios científicos respaldan el uso combinado de prefiltrado, sedimentación, arena y carbón activado para reducir turbidez y ciertos contaminantes de aguas grises.

ExpoClean debe completar esa validación externa con pruebas propias de volumen, turbidez, caudal y repetibilidad. De esta manera, la propuesta no se limita a afirmar que la tecnología existe: demuestra qué parte del desempeño fue comprobada, qué parte se encuentra en desarrollo y cuáles son las limitaciones del prototipo.
