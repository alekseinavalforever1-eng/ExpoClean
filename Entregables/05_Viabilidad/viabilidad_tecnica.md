# Viabilidad técnica y económica de las soluciones ExpoClean

## 1. Resumen ejecutivo

ExpoClean propone dos prototipos complementarios:

1. **Solución 1 — Filtración y pretratamiento de aguas grises.** Separa residuos gruesos, sedimenta sólidos, filtra el agua con grava, arena y carbón activado, y monitorea la turbidez mediante un ESP32.
2. **Solución 2 — Dosificación inteligente.** Extrae producto desde un bidón y dispensa un volumen programado mediante una bomba de 12 V controlada por ESP32, relé y aplicación web.

Ambas soluciones presentan **viabilidad técnica para una fase de prototipo** porque utilizan componentes comerciales, de bajo costo y relativamente fáciles de integrar. La dosificación tiene una ruta de implementación más sencilla y puede validarse rápidamente. La filtración también es viable como pretratamiento experimental, pero requiere más pruebas para definir el caudal, el tiempo de sedimentación, la saturación de los medios y la calidad final del agua.

Los presupuestos actualizados son:

| Solución | Inversión estimada de materiales | Con contingencia del 10% |
|---|---:|---:|
| Solución 1: filtración | **USD 88,75–118,75** | **USD 97,63–130,63** |
| Solución 2: dosificación | **USD 75,80–103,80** | **USD 83,38–114,18** |
| **Ambas soluciones** | **USD 164,55–222,55** | **USD 181,01–244,81** |

> La suma de ambas soluciones con una contingencia del 10% se calcula sobre el subtotal total: USD 164,55–222,55 × 1,10 = **USD 181,01–244,81**.

Los valores son presupuestos preliminares con precios de catálogo y estimaciones de materiales. No incluyen mano de obra, transporte, impuestos no indicados, pruebas de laboratorio, desarrollo de software, certificaciones ni mantenimiento.

## 2. Criterios utilizados

La viabilidad se evaluó con cinco criterios:

- **Disponibilidad:** los componentes pueden conseguirse comercialmente en Ecuador o reemplazarse por equivalentes.
- **Complejidad:** el sistema puede construirse con conocimientos de electrónica básica, programación e instalación hidráulica.
- **Costo:** la inversión es adecuada para una prueba de concepto y un prototipo funcional.
- **Validación:** existen mediciones concretas para saber si funciona.
- **Escalabilidad:** la arquitectura permite agregar bombas, sensores, depósitos y registros digitales.

## 3. Solución 1 — Sistema de filtración y pretratamiento

### 3.1 Viabilidad técnica

La solución es técnicamente viable como un sistema de **pretratamiento físico**. Su funcionamiento se basa en operaciones conocidas y fáciles de observar:

```text
Agua gris → malla → sedimentación → grava/arena/carbón activado
          → bombeo → sensor de turbidez → almacenamiento
```

La parte hidráulica puede construirse con recipientes plásticos, mangueras, válvulas y materiales filtrantes. La parte electrónica se limita a controlar una bomba y recibir la lectura del sensor de turbidez.

La principal incertidumbre no es si el agua puede pasar por el filtro, sino **qué calidad tendrá el agua de salida y durante cuánto tiempo se mantendrá el rendimiento**. El tipo de suciedad, la concentración de detergente, el caudal y el taponamiento pueden cambiar los resultados.

### 3.2 Presupuesto de materiales

| Componente | Cantidad / descripción | Precio estimado (USD) | Tipo de costo |
|---|---|---:|---|
| ESP32 USB-C | Controlador | 11,00 | Catálogo SIEC |
| Bomba de diafragma 12 V | Impulsa el agua filtrada | 8,00 | Catálogo Pro Electronics |
| Sensor de turbidez | Mide claridad del agua | 19,95 | Catálogo Megatrónica |
| Relé de un canal 5 V | Control eléctrico de la bomba | 2,80 | Catálogo SIEC |
| Fuente 12 V, 5 A | Alimentación | 11,00 | Catálogo Pro Electronics |
| Recipientes plásticos | Entrada, sedimentación y salida | 10,00–18,00 | Estimación |
| Grava, arena y carbón activado | Medios filtrantes | 8,00–15,00 | Estimación |
| Mangueras, válvulas y mallas | Conducción y separación | 8,00–15,00 | Estimación |
| Base, cables y protección | Montaje físico y eléctrico | 10,00–18,00 | Estimación |
| **Total corregido** |  | **88,75–118,75** |  |

El total superior se corrige a **USD 118,75**. La suma de los valores publicados y estimados es:

```text
11 + 8 + 19,95 + 2,80 + 11
+ (10–18) + (8–15) + (8–15) + (10–18)
= USD 88,75–118,75
```

### 3.3 Viabilidad operativa

La solución puede construirse como módulo independiente y probarse por lotes. Para una primera demostración no es necesario automatizar todas las etapas: la malla, la sedimentación y el filtro pueden operar por gravedad, mientras la bomba se utiliza para trasladar el agua al depósito final.

Esto reduce el riesgo de la primera versión. Después se pueden agregar sensores de nivel, caudal o pH.

### 3.4 Costos no incluidos

- Reemplazo periódico de arena y carbón activado.
- Limpieza de recipientes, mallas y tuberías.
- Tratamiento o disposición de los lodos.
- Medición de DQO, DBO, sólidos suspendidos, surfactantes o microbiología.
- Diseño de una carcasa permanente y resistente a químicos.
- Transporte, conectores adicionales y herramientas.

Las pruebas de laboratorio pueden costar más que los componentes electrónicos; por eso deben presupuestarse como una fase de validación, no mezclarse con el costo de construcción del prototipo.

### 3.5 Riesgos y mitigación

| Riesgo | Efecto | Mitigación |
|---|---|---|
| Taponamiento del filtro | Disminuye el caudal y aumenta el tiempo de proceso. | Prefiltro removible, medición de caudal y mantenimiento programado. |
| Variación del agua de entrada | Resultados diferentes entre pruebas. | Preparar muestras comparables y registrar origen del agua. |
| Sensor de turbidez inestable | Lecturas poco confiables. | Calibrar, repetir mediciones y comparar con una escala o instrumento de referencia. |
| Agua visualmente clara pero contaminada | Falsa percepción de seguridad. | No declarar reúso sin análisis de calidad. |
| Saturación del carbón activado | Menor adsorción de compuestos y olores. | Registrar ciclos de uso y establecer reemplazo del medio. |

## 4. Solución 2 — Estación inteligente de dosificación

### 4.1 Viabilidad técnica

La dosificación tiene una viabilidad técnica alta para prototipo. La arquitectura es directa:

```text
Aplicación web → ESP32 → relé → bomba de 12 V → manguera → boquilla
```

El primer prototipo puede funcionar con dosificación por tiempo, siempre que la bomba se calibre antes de utilizarla. En una versión posterior, un sensor de flujo puede sustituir o complementar la estimación por tiempo.

### 4.2 Presupuesto de materiales

| Componente | Cantidad / descripción | Precio estimado (USD) | Tipo de costo |
|---|---|---:|---|
| ESP32 USB-C | Controlador | 11,00 | Catálogo SIEC |
| Bomba peristáltica 3–12 V | Dosificación del producto | 12,00 | Catálogo Pro Electronics |
| Relé de un canal | Control eléctrico de la bomba | 2,80 | Catálogo SIEC |
| Fuente 12 V, 5 A | Alimentación | 11,00 | Catálogo Pro Electronics |
| Bidón, mangueras y boquilla | Conducción del producto | 14,00–24,00 | Estimación |
| Estructura de madera y bandeja | Soporte físico | 20,00–35,00 | Estimación |
| Cableado y protección | Conexiones y seguridad eléctrica | 5,00–8,00 | Estimación |
| **Total corregido** |  | **75,80–103,80** |  |

El total superior se corrige a **USD 103,80**. La suma es:

```text
11 + 12 + 2,80 + 11
+ (14–24) + (20–35) + (5–8)
= USD 75,80–103,80
```

La bomba económica de USD 12 puede utilizarse para la primera prueba, pero su caudal real debe medirse. La precisión final dependerá de la altura de succión, la viscosidad del producto, el diámetro de la manguera, el nivel del bidón y el desgaste de la bomba.

### 4.3 Viabilidad operativa

La demostración puede implementarse en etapas:

1. Calibrar la bomba con agua.
2. Controlar el encendido y apagado desde el ESP32.
3. Sustituir el agua por el producto compatible para la prueba.
4. Medir la dosis con una probeta.
5. Conectar el registro de la orden a la aplicación web.

No es necesario construir desde el inicio una estación con múltiples bidones. La primera versión puede utilizar una sola línea de dosificación y demostrar la posibilidad de ampliación.

### 4.4 Costos no incluidos

- Desarrollo y mantenimiento de la aplicación web.
- Hosting o servidor, si se utiliza un servicio de pago.
- Sensor de flujo para medición volumétrica directa.
- Más bombas y líneas para varios productos.
- Depósitos compatibles con cada químico.
- Etiquetas, QR, pantalla o lector dedicado.
- Pruebas de compatibilidad química y seguridad.

### 4.5 Riesgos y mitigación

| Riesgo | Efecto | Mitigación |
|---|---|---|
| Caudal variable | Dosis diferente con el mismo tiempo. | Calibrar antes de cada prueba y añadir sensor de flujo en la siguiente versión. |
| Producto viscoso | La bomba entrega menos volumen. | Calibrar con el producto real, no solo con agua. |
| Goteo posterior | Dosis superior a la programada. | Utilizar válvula antirretorno, boquilla adecuada y bandeja antigoteo. |
| Incompatibilidad química | Daño de mangueras o reacciones peligrosas. | Probar un solo producto compatible y no mezclar químicos. |
| Falla eléctrica | Daño de la bomba o del controlador. | Fuente adecuada, fusible, aislamiento y protección contra derrames. |

## 5. Comparación económica y prioridad

| Criterio | Filtración | Dosificación |
|---|---|---|
| Inversión estimada | USD 88,75–118,75 | USD 75,80–103,80 |
| Complejidad de integración | Media | Baja-media |
| Tiempo para demostrar | Mayor, por sedimentación y filtración | Menor, por calibración y bombeo |
| Resultado principal | Reducción de turbidez y separación de sólidos | Exactitud y repetibilidad de dosis |
| Riesgo principal | Calidad variable y saturación del filtro | Variación del caudal |
| Validación requerida | Turbidez, caudal, sólidos y posible calidad de reúso | Volumen medido, error y repetibilidad |
| Prioridad recomendada | Segunda fase experimental | Primera demostración funcional |

### Recomendación de inversión

Para el hackathon se recomienda priorizar la Solución 2 porque requiere menos componentes, tiene una prueba de éxito más directa y puede mostrar rápidamente una acción controlada: solicitar una cantidad, activar la bomba, medir el volumen y registrar el resultado.

La Solución 1 debe presentarse como un prototipo de pretratamiento con alto valor ambiental, pero con una validación más cuidadosa. Su costo sigue siendo accesible; lo que aumenta la incertidumbre no es el precio del filtro, sino la necesidad de caracterizar la calidad del agua antes de afirmar que puede reutilizarse.

## 6. Escenarios de implementación

### Escenario A — Demostración mínima

Se construye una línea de dosificación y una unidad básica de filtración con materiales disponibles.

```text
Costo de materiales: USD 164,55–222,55
Costo con contingencia del 10%: USD 181,01–244,81
```

### Escenario B — Prototipo mejorado

Se incorporan sensor de flujo para la dosificación, sensores de nivel, mejor protección eléctrica, estructura más resistente y mediciones de calidad del agua.

El costo debe cotizarse después de seleccionar los sensores y el alcance de laboratorio. No conviene presentar un precio único sin contar con esas cotizaciones.

### Escenario C — Piloto operativo

Requiere, además de los materiales:

- pruebas repetidas con agua real;
- mantenimiento y reposición de filtros;
- capacitación del operario;
- registro de resultados por jornada;
- análisis de laboratorio para decidir sobre reúso o descarga;
- revisión de requisitos regulatorios aplicables.

## 7. Conclusión

Las dos soluciones son viables para construir y validar como prototipos. La estación de dosificación tiene mayor viabilidad inmediata porque su función puede comprobarse con una medición sencilla de volumen y tiempo. El sistema de filtración es viable como pretratamiento modular, pero su desempeño depende de la composición del agua, el diseño del medio filtrante, el caudal y el mantenimiento.

Con los precios consultados, ExpoClean puede construir ambos prototipos con una inversión aproximada de **USD 164,55 a USD 222,55 en materiales**, o **USD 181,01 a USD 244,81 incluyendo una contingencia del 10%**. Estos montos son adecuados para una prueba de concepto, pero no representan todavía el costo de una solución industrial final.

La siguiente decisión recomendada es comprar primero los componentes de la estación dosificadora, calibrar la bomba y generar la primera evidencia de exactitud. Paralelamente, se puede construir el filtro y validar su reducción de turbidez con pruebas controladas.
