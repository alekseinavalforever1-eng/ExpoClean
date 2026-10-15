# Propuesta de valor — ExpoClean

## Cliente objetivo

Empresas pequeñas y medianas de limpieza profesional en Ecuador, equipos de mantenimiento y administradores de instalaciones que consumen productos de limpieza de forma recurrente.

El comprador probable es el propietario, gerente de operaciones o responsable de mantenimiento. Los supervisores y operarios son los usuarios directos del sistema.

## Problema

La dosificación manual produce variaciones entre operarios, desperdicio potencial de productos químicos y ausencia de registros por servicio. Además, el agua utilizada en la limpieza puede contener sólidos, sedimentos y residuos de detergentes, pero normalmente no se separa ni se monitorea antes de su descarga.

## Solución

### Módulo Refill — Dosificación inteligente

Una aplicación web permite solicitar una cantidad de producto. El ESP32 activa una bomba de 12 V durante el tiempo calculado a partir del caudal calibrado. La operación queda registrada y puede compararse con el método manual.

### Módulo Agua — Pretratamiento de aguas grises

Una unidad modular utiliza malla, sedimentación, grava, arena y carbón activado para disminuir sólidos y turbidez. Un sensor registra la claridad del agua antes y después del proceso.

Este módulo es un **prototipo de pretratamiento**. No garantiza potabilidad, eliminación total de contaminantes ni cumplimiento automático de límites de descarga.

## Beneficio comprobable

Los pilotos deben medir:

- error entre la dosis solicitada y el volumen dispensado;
- consumo de producto por operación;
- reducción de producto frente al método manual;
- turbidez de entrada y salida;
- litros procesados por hora;
- frecuencia de mantenimiento;
- costo de operación por cliente.

## Hipótesis comerciales

- **Reducción de costo de químicos:** se plantea como objetivo de validación, no como ahorro demostrado.
- **Suscripción de USD 50–200/mes:** rango inicial para entrevistas y pruebas de disposición a pagar.
- **FEDELIMP/JIMCORPSERVI:** canales o aliados potenciales, no convenios confirmados.
- **Reportes ambientales:** trazabilidad operativa; no equivalen por sí solos a certificación ni cumplimiento regulatorio.

## Oferta inicial

Se propone un piloto de 30 días con:

- una línea de dosificación;
- instalación y calibración;
- capacitación básica;
- dashboard de consumo;
- comparación entre método manual y método controlado;
- informe de resultados.

El hardware y la instalación se cotizan por separado. El módulo hídrico se ofrece inicialmente como demostración o servicio de evaluación hasta contar con resultados suficientes de calidad del agua.

## Validación de mercado

Antes de fijar el precio definitivo se recomienda:

1. entrevistar al menos cinco empresas de limpieza;
2. registrar consumo mensual de químicos, gasto y frecuencia de servicios;
3. identificar quién decide la compra y qué problema prioriza;
4. ejecutar uno o dos pilotos;
5. comparar indicadores antes/después;
6. preguntar cuánto pagarían por hardware, instalación, software y soporte;
7. buscar una carta de intención o compromiso de piloto, sin presentarla como contrato.

