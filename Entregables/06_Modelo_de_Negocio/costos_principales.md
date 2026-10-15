# Costos principales — ExpoClean

> Valores preliminares para Ecuador. Son referencias de planificación y estimaciones, no cotizaciones definitivas ni promesas de rentabilidad.

## Hardware de prototipo

| Concepto | Dosificación | Filtración |
|---|---:|---:|
| Electrónica, bomba, control, fuente y sensor | USD 35–37 | USD 52,75 |
| Recipientes, mangueras, válvulas y medios | USD 14–24 | USD 36–66 |
| Estructura, base, cables y protección | USD 25–43 | Incluidos en el rango anterior |
| **Total corregido** | **USD 75,80–103,80** | **USD 88,75–118,75** |

El costo conjunto de materiales se estima en **USD 164,55–222,55**. Con una contingencia del 10% para variaciones de precio, reemplazos y conexiones adicionales, el presupuesto recomendado es **USD 181,01–244,81**.

### Consideraciones

- El gabinete con lector QR físico, pantalla LCD y dos boquillas tiene un costo superior al MVP.
- Para el primer piloto se recomienda usar QR impreso, celular y una sola línea de dosificación.
- En filtración se recomienda iniciar con recipientes plásticos y medios filtrantes reemplazables antes de fabricar una estructura definitiva.
- Los precios de catálogo deben confirmarse antes de comprar; la disponibilidad puede cambiar.

## Operación mensual del MVP

| Concepto | Estimación | Observación |
|---|---:|---|
| Hosting web/backend | USD 0–50/mes | Depende del tráfico y del proveedor. |
| Dominio | USD 1–2/mes equivalente | Aproximadamente USD 12–24 al año. |
| Monitoreo y mensajería | USD 0–20/mes | Según consumo. |
| Mantenimiento de software | Variable | Debe presupuestarse como horas reales. |
| Soporte y desplazamientos | Variable | Depende de instalaciones y clientes. |
| Material filtrante y residuos | Variable | Aplica principalmente al módulo de agua. |
| Pruebas de laboratorio | Variable | Necesarias para afirmar calidad, reúso o descarga. |
| Marketing inicial | USD 100–500 | Presupuesto de lanzamiento, no costo mensual fijo. |

La base de cloud, dominio y mensajería puede ubicarse aproximadamente entre **USD 1 y USD 72 al mes**, antes de sumar soporte, sueldos, mantenimiento, ensayos, hardware y marketing. Por esa razón no se debe afirmar que el costo operativo total es de USD 50–100 mensuales.

## Ingresos propuestos

- Suscripción SaaS: **USD 50–200 por empresa al mes**, como hipótesis inicial.
- Venta o arriendo de hardware con margen calculado sobre costo completo.
- Instalación y calibración como cobro único.
- Mantenimiento y soporte técnico.
- Servicio de evaluación hídrica y coordinación de ensayos con laboratorios competentes.

## Unidad económica

```text
Margen de contribución mensual por cliente =
precio de suscripción - costos variables del cliente

Punto de equilibrio =
costos fijos mensuales / margen de contribución por cliente
```

### Ejemplo hipotético

```text
Tarifa mensual:              USD 75
Costos variables por cliente: USD 20
Costos fijos mensuales:      USD 275
Margen de contribución:      USD 55
Punto de equilibrio:         275 / 55 = 5 clientes
```

Este ejemplo no incluye impuestos, amortización del hardware, sueldos ni recuperación de la inversión inicial. Debe reemplazarse por datos reales después del piloto.

## Costos de una implementación comercial

Una versión comercial tendrá costos adicionales respecto al prototipo:

- gabinete resistente a humedad y químicos;
- sensor de flujo y sensores de nivel;
- protecciones eléctricas y certificación del montaje;
- instalación y garantía;
- mantenimiento y reposición de bombas;
- desarrollo de usuarios, roles, reportes y respaldo de datos;
- pruebas de compatibilidad química;
- análisis de laboratorio para el módulo hídrico.

## Recomendación comercial

La primera oferta debería venderse como **piloto de dosificación y trazabilidad**, porque tiene un resultado más fácil de medir. El módulo de filtración debe presentarse inicialmente como una solución de pretratamiento en evaluación, con cobro por piloto o servicio técnico, hasta demostrar la calidad del agua de salida en condiciones reales.
