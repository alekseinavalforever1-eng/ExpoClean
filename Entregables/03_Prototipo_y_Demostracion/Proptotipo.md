# Prototipos y demostración de ExpoClean

## 1. Descripción general

ExpoClean se materializa en dos prototipos complementarios que responden al Reto 4 desde dos momentos del proceso de limpieza:

1. **Solución 1 — Sistema de filtración y pretratamiento de aguas grises:** recibe el agua utilizada, separa residuos sólidos, reduce la turbidez mediante filtración multietapa y monitorea el proceso.
2. **Solución 2 — Estación inteligente de dosificación:** entrega una cantidad controlada de producto de limpieza mediante una bomba de 12 V controlada por un ESP32 y una aplicación web.

La primera solución interviene después del servicio de limpieza; la segunda interviene antes y durante la preparación del producto. En conjunto, permiten reducir desperdicios en el origen y gestionar mejor el agua residual generada.

> Las imágenes representan el diseño y funcionamiento esperado de los prototipos. Durante la demostración se validarán únicamente los componentes que estén físicamente instalados y operativos.

---

## 2. Solución 1: sistema de filtración y pretratamiento de aguas grises

### 2.1 Descripción del prototipo

El prototipo de filtración es un sistema compacto y modular para tratar de manera preliminar el agua utilizada durante actividades de limpieza, especialmente agua de trapeado.

El sistema combina una malla de prefiltrado, una cámara de sedimentación, un filtro multietapa, una bomba de 12 V y un sensor de turbidez conectado a un ESP32. El agua procesada se almacena en un recipiente independiente para evaluar su posible reutilización en tareas de limpieza no críticas.

![Solución 1: sistema de filtración y pretratamiento de aguas grises](../02_Propuesta_de_Solucion/assets/Solucion_filtrado.png)

*Figura 1. Flujo conceptual del prototipo de filtración: entrada, prefiltrado, sedimentación, filtración, bombeo y almacenamiento.*

### 2.2 Funcionamiento del prototipo

#### Etapa 1. Entrada de agua de trapeador

El operario deposita el agua utilizada en un recipiente de entrada. Esta agua puede contener tierra, polvo, cabellos, arena, fibras, grasas, partículas orgánicas y restos de detergentes o desinfectantes.

#### Etapa 2. Pre-filtrado de residuos gruesos

El agua pasa por una malla removible que retiene hojas, cabellos, piedras, fibras y otros residuos de mayor tamaño. La malla evita que estos materiales ingresen a las etapas posteriores y puede retirarse para su limpieza.

#### Etapa 3. Sedimentación

El agua ingresa a una cámara de reposo. Por efecto de la gravedad, las partículas pesadas se depositan en el fondo y forman sedimentos o lodos. Estos residuos se retiran mediante una salida inferior y se almacenan en un recipiente independiente.

#### Etapa 4. Filtración multietapa

El agua parcialmente clarificada atraviesa diferentes materiales filtrantes:

- **Grava:** retiene partículas de mayor tamaño y ayuda a distribuir el flujo.
- **Arena gruesa:** retiene sólidos intermedios.
- **Arena fina:** retiene partículas suspendidas más pequeñas.
- **Carbón activado:** puede adsorber determinados compuestos orgánicos, olores y parte de ciertos residuos químicos, dependiendo de la composición del agua y del tiempo de contacto.
- **Malla de soporte:** evita que el material filtrante sea arrastrado hacia la salida.

#### Etapa 5. Bombeo y monitoreo

Una bomba eléctrica de 12 V impulsa el agua filtrada hacia el depósito final. El ESP32 controla la activación y desactivación de la bomba.

El sensor de turbidez mide un indicador de la claridad del agua y transmite los datos a la aplicación web. La aplicación puede mostrar la medición, registrar la duración del ciclo, consultar el estado del sistema y comparar el agua de entrada con el agua de salida.

#### Etapa 6. Almacenamiento

El agua procesada se deposita en un recipiente independiente. El resultado esperado es una reducción de sólidos suspendidos y turbidez respecto al agua inicial.

El agua no se considera automáticamente potable ni apta para cualquier uso. Su posible reutilización se limita a actividades no críticas y debe depender de las mediciones de calidad obtenidas.

### 2.3 Componentes principales

| Componente | Función |
|---|---|
| Recipiente de entrada | Recibe temporalmente el agua utilizada. |
| Malla de prefiltrado | Retiene residuos gruesos. |
| Cámara de sedimentación | Separa partículas pesadas por gravedad. |
| Recipiente de lodos | Recoge los sedimentos separados. |
| Grava y arena | Retienen sólidos suspendidos. |
| Carbón activado | Adsorbe determinados compuestos y olores. |
| Bomba de 12 V | Transporta el agua hacia el depósito final. |
| ESP32 | Controla la bomba y recibe datos del sensor. |
| Sensor de turbidez | Monitorea la claridad del agua. |
| Mangueras y conexiones | Conducen el agua entre las etapas. |
| Aplicación web | Visualiza y registra el ciclo de filtración. |

### 2.4 Demostración de la Solución 1

La demostración seguirá este procedimiento:

1. Preparar un volumen conocido de agua con residuos representativos de una limpieza.
2. Medir y registrar la turbidez inicial.
3. Introducir el agua en el recipiente de entrada.
4. Observar la retención de residuos en la malla.
5. Mostrar la acumulación de sedimentos en la cámara de sedimentación.
6. Activar la bomba y conducir el agua por el filtro multietapa.
7. Medir y registrar la turbidez de salida.
8. Comparar los valores de entrada y salida en la aplicación.
9. Almacenar el agua filtrada para evaluar si puede utilizarse en una tarea de limpieza no crítica.

Indicador principal:

```text
Reducción de turbidez (%) =
(turbidez inicial - turbidez final) / turbidez inicial × 100
```

La prueba demostrará la separación de residuos y la reducción de turbidez. No demostrará por sí sola la eliminación completa de detergentes, cloro, microorganismos o sustancias disueltas.

---

## 3. Solución 2: estación inteligente de dosificación

### 3.1 Descripción del prototipo

El segundo prototipo es una estación de dosificación de productos de limpieza. Está diseñada para entregar una cantidad controlada de producto desde un bidón hacia un recipiente de usuario, evitando que el operario vierta el químico “al ojo”.

La estación integra un bidón de aproximadamente 10–20 litros, mangueras, una bomba de 12 V, un relé, un ESP32, una fuente de alimentación, una o más boquillas y una aplicación web. La imagen muestra también un lector QR y una pantalla para orientar al usuario durante el proceso.

![Solución 2: estación inteligente de dosificación](../02_Propuesta_de_Solucion/assets/Solucion_dosificador.jpeg)

*Figura 2. Diseño conceptual de la estación de dosificación con bidón, electrónica, bomba, lector QR, pantalla y boquillas de salida.*

### 3.2 Funcionamiento del prototipo

1. **Ingreso del producto.** Se coloca el bidón de producto de limpieza en el compartimento lateral y se conecta la manguera a la bomba.
2. **Identificación.** El usuario escanea el código QR de la estación para acceder a la aplicación web de ExpoClean.
3. **Selección de la cantidad.** El usuario solicita el volumen de producto que necesita. En una versión ampliada, la aplicación puede calcular la dosis a partir del área, el tipo de superficie, el nivel de suciedad y la dilución recomendada.
4. **Cálculo del tiempo.** La aplicación convierte el volumen solicitado en un tiempo de activación utilizando el caudal calibrado de la bomba.
5. **Activación.** La orden llega al ESP32, que activa el relé y enciende la bomba de 12 V.
6. **Dispensación.** La bomba extrae el producto del bidón y lo conduce por la manguera hasta la boquilla de salida.
7. **Finalización.** Al cumplirse el tiempo programado, el ESP32 desactiva el relé y detiene la bomba.
8. **Registro.** La aplicación guarda la cantidad estimada, el producto utilizado, el ciclo ejecutado y la fecha.

### 3.3 Calibración de la bomba

En el prototipo inicial, el volumen se controla mediante el tiempo de funcionamiento de la bomba. Para calibrarla se recoge el líquido durante un tiempo conocido y se mide el volumen entregado.

```text
Caudal calibrado = volumen medido / tiempo de activación
Tiempo requerido = volumen solicitado / caudal calibrado
```

Ejemplo:

```text
Volumen solicitado: 20 mL
Caudal calibrado:    5 mL/s
Tiempo requerido:    4 s
```

Esta estrategia es una estimación basada en la calibración. Para mejorar la exactitud se puede incorporar un sensor de flujo que mida el volumen real y detenga la bomba automáticamente al alcanzar la cantidad solicitada.

### 3.4 Componentes principales

| Componente | Función |
|---|---|
| Bidón de producto | Almacena el detergente o producto seleccionado. |
| Mangueras | Transportan el líquido desde el bidón hasta la salida. |
| Bomba de 12 V | Impulsa el producto durante el tiempo programado. |
| Relé | Actúa como interruptor de la bomba. |
| ESP32 | Recibe la orden y controla el ciclo de dispensación. |
| Fuente de alimentación | Proporciona energía al sistema electrónico y a la bomba. |
| Boquilla de salida | Entrega el producto en el recipiente del usuario. |
| Lector QR | Permite identificar la estación desde la aplicación. |
| Pantalla | Muestra instrucciones o mensajes simples al usuario. |
| Aplicación web | Permite solicitar dosis y registrar el consumo. |
| Bandeja antigoteo | Reduce derrames y facilita la limpieza de la estación. |

### 3.5 Demostración de la Solución 2

La demostración seguirá este procedimiento:

1. Mostrar el bidón conectado a la bomba y a la boquilla.
2. Escanear el código QR o ingresar a la aplicación.
3. Solicitar una dosis conocida, por ejemplo, 20 mL.
4. Mostrar el caudal calibrado y el tiempo calculado.
5. Enviar la orden al ESP32.
6. Observar la activación de la bomba y la salida del producto.
7. Medir la cantidad entregada con una probeta o recipiente graduado.
8. Comparar el volumen solicitado con el volumen medido.
9. Mostrar el registro generado en la aplicación.

Indicador principal:

```text
Exactitud de dosificación (%) =
volumen medido / volumen solicitado × 100
```

La demostración comprobará el control automático de una línea de dosificación. Si todavía no están instaladas dos bombas o un sensor de flujo, no se debe afirmar que la estación mide directamente el volumen ni que todas las boquillas funcionan de manera independiente.

---

## 4. Integración de los prototipos

Los prototipos se complementan dentro del ciclo de limpieza:

```text
Solución 2: dosificación controlada
        ↓
Uso preciso de productos químicos
        ↓
Servicio de limpieza
        ↓
Generación de agua gris
        ↓
Solución 1: filtración y monitoreo
        ↓
Evaluación de turbidez y posible reúso no crítico
```

La dosificación reduce la cantidad innecesaria de químico que llega al agua residual. La filtración posterior separa residuos sólidos y sedimentos, mientras el sensor de turbidez permite medir el cambio visual y físico del agua durante el proceso.

## 5. Resultados esperados

Con estos prototipos se busca demostrar:

- dosificación repetible de una cantidad definida de producto;
- reducción de la variabilidad del método manual;
- registro digital de los ciclos de dosificación y filtración;
- separación de residuos gruesos y sedimentos del agua de trapeador;
- reducción medible de turbidez después de la filtración;
- viabilidad de una arquitectura modular con ESP32, bombas y sensores;
- posibilidad de evaluar el reúso de agua únicamente en actividades no críticas y con validación de calidad.

## 6. Limitaciones y seguridad

- El sistema de filtración es un **pretratamiento**, no una planta de potabilización.
- La turbidez no representa por sí sola la totalidad de la contaminación del agua.
- El carbón activado no elimina automáticamente todos los detergentes, desinfectantes o sustancias disueltas.
- Los filtros requieren limpieza, mantenimiento y reemplazo periódico.
- No se deben mezclar cloro, ácidos, detergentes u otros productos incompatibles.
- El agua filtrada no debe utilizarse para consumo humano ni para procesos críticos sin análisis y autorización correspondientes.
- Los valores finales de reducción de turbidez y exactitud de dosificación deben obtenerse mediante pruebas experimentales.
