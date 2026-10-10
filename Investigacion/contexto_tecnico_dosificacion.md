# 🧪 Contexto Técnico: Dosificación Inteligente y Tratamiento de Aguas Grises

> Documento de fundamentación técnica para el prototipo/simulación del Reto 4.
> Incluye las fórmulas, parámetros y lógica que deben implementarse en la calculadora/dashboard.

---

## 1. Fundamentos de la Dosificación en Limpieza Industrial

### 1.1 ¿Qué es la Dosificación?

La dosificación es el proceso de preparar una **solución de limpieza** mezclando un **agente limpiador concentrado** (detergente, desinfectante, desengrasante) con **agua** en una proporción específica llamada **relación de dilución**.

### 1.2 El Problema Actual: Dosificación Empírica

En la mayoría de empresas de limpieza PYME, la dosificación se realiza:

- **"Al ojo":** El operario vierte concentrado directamente en un balde con agua sin medir.
- **Sin considerar el contexto:** La misma cantidad de detergente se usa para 10 m² que para 100 m², para pisos ligeramente sucios que para cocinas industriales con grasa.
- **Sin registro:** No queda evidencia de cuánto producto se usó, lo que impide auditar, optimizar o reportar.

### 1.3 Consecuencias Documentadas

| Consecuencia | Impacto |
|---|---|
| **Sobredosificación** (lo más común) | Desperdicio de 20-40% de producto. Mayor carga química en el efluente. Residuo pegajoso en superficies que atrae más suciedad. |
| **Subdosificación** | Limpieza deficiente. Necesidad de re-limpiar (más agua, más producto, más tiempo). |
| **Efluente descontrolado** | Imposible estimar la carga contaminante. Incumplimiento potencial de TULSMA. |
| **Sobrecostos** | El producto químico es el segundo costo operativo después de la mano de obra. |

---

## 2. Modelo Matemático de Dosificación Parametrizada

### 2.1 Variables de Entrada

| Variable | Símbolo | Unidad | Fuente del dato |
|---|---|---|---|
| Área a limpiar | `A` | m² | Ingresada por el operario/supervisor |
| Tipo de superficie | `Fs` | adimensional | Tabla predefinida en el sistema |
| Nivel de suciedad | `Fn` | adimensional | Selección del operario (4 niveles) |
| Rendimiento hídrico | `Rh` | L/m² | Dato técnico por tipo de proceso |
| Dilución recomendada del producto | `D` | % (v/v) | Ficha técnica del fabricante |
| Concentración DQO del producto | `DQO_p` | mg/L (puro) | Ficha técnica / SDS |
| pH del producto | `pH_p` | — | Ficha técnica / SDS |

### 2.2 Tablas de Factores

#### Factor de Superficie (`Fs`)

| Superficie | Factor | Justificación |
|---|---|---|
| Cerámica / Porcelanato | 1.0 | Referencia base, baja porosidad |
| Concreto / Cemento | 1.3 | Mayor porosidad, absorbe más solución |
| Acero inoxidable | 0.8 | Liso, requiere menos solución |
| Madera tratada | 1.2 | Porosa pero no tanto como concreto |
| Vidrio | 0.7 | Muy liso, mínima retención |
| Alfombra / Textil | 1.8 | Alta absorción |

#### Factor de Suciedad (`Fn`)

| Nivel | Factor | Descripción |
|---|---|---|
| Leve | 0.7 | Polvo superficial, mantenimiento diario |
| Medio | 1.0 | Suciedad visible, limpieza regular |
| Pesado | 1.5 | Grasa, manchas adheridas |
| Extremo | 2.0 | Acumulación severa, post-construcción, derrames |

#### Rendimiento Hídrico (`Rh`) por Tipo de Proceso

| Proceso de limpieza | Rh (L/m²) | Notas |
|---|---|---|
| Fregado manual (mopa/trapo) | 0.10 – 0.20 | Bajo consumo de agua |
| Fregado con máquina scrubber | 0.15 – 0.30 | Depende del modelo |
| Lavado con hidrolavadora | 0.30 – 0.50 | Mayor consumo |
| Limpieza de cocina industrial | 0.25 – 0.40 | Enjuague abundante |
| Lavado de vehículos | 0.40 – 0.80 | Alto consumo |

### 2.3 Fórmulas del Sistema

#### Cálculo del Volumen de Agua

```
V_agua = A × Fs × Fn × Rh
```

Donde:
- `V_agua` = Volumen de agua necesario (Litros)
- `A` = Área en m²
- `Fs` = Factor de superficie
- `Fn` = Factor de nivel de suciedad
- `Rh` = Rendimiento hídrico (L/m²)

**Ejemplo:** 200 m² de cerámica con suciedad media, fregado manual (Rh=0.15):
```
V_agua = 200 × 1.0 × 1.0 × 0.15 = 30 Litros
```

#### Cálculo del Volumen de Producto Concentrado

```
V_producto = V_agua × (D / 100)
```

Donde:
- `V_producto` = Volumen de producto concentrado necesario (Litros)
- `D` = Dilución recomendada (% v/v)

**Ejemplo:** Si el producto se diluye al 2% (1:50):
```
V_producto = 30 × (2 / 100) = 0.6 Litros = 600 mL
```

#### Volumen Total de Solución

```
V_solución = V_agua + V_producto
```

**Ejemplo:**
```
V_solución = 30 + 0.6 = 30.6 Litros
```

---

## 3. Estimación de la Carga Contaminante del Efluente

### 3.1 ¿Por qué es Importante?

Al conocer **exactamente** qué y cuánto se dosificó, podemos **predecir** la composición del agua residual (efluente) sin necesidad de un laboratorio. Esto permite:

1. Dimensionar el pre-tratamiento necesario.
2. Verificar cumplimiento normativo (TULSMA).
3. Generar reportes de desempeño ambiental automáticos.

### 3.2 Fórmulas de Estimación

#### DQO del Efluente

```
DQO_efluente = (V_producto × DQO_p) / V_solución + DQO_suciedad
```

Donde:
- `DQO_p` = DQO del producto puro (dato de ficha técnica/SDS, típicamente 10.000 – 100.000 mg/L para concentrados)
- `DQO_suciedad` = Aporte estimado de materia orgánica de la suciedad removida (depende del tipo)

| Tipo de suciedad | DQO_suciedad estimada (mg/L en efluente) |
|---|---|
| Polvo / tierra | 50 – 150 |
| Grasa alimentaria | 200 – 500 |
| Residuo orgánico | 150 – 400 |
| Residuo industrial | 300 – 1000 |

**Ejemplo:** Producto con DQO_p = 50.000 mg/L, suciedad media (DQO_suciedad = 200 mg/L):
```
DQO_efluente = (0.6 × 50.000) / 30.6 + 200
             = 980 + 200
             = 1.180 mg/L
```

#### Tensoactivos (Surfactantes)

```
Tensoactivos_efluente = (V_producto × Conc_surfactante_producto) / V_solución
```

Los límites TULSMA para tensoactivos son típicamente < 0.5 mg/L para descarga a cuerpos de agua dulce.

#### pH del Efluente

```
pH_efluente ≈ pH_producto + log10(Factor_dilución)
```

Para productos alcalinos (pH_producto > 10), la dilución alta (1:50) típicamente lleva el pH a rangos de 8-9, cercanos al límite TULSMA (6-9).

### 3.3 Comparación con Límites TULSMA

El sistema puede generar automáticamente una tabla como esta:

| Parámetro | Valor Estimado | Límite TULSMA (alcantarillado) | Estado |
|---|---|---|---|
| DQO | 1.180 mg/L | 500 mg/L | ⚠️ Requiere pre-tratamiento |
| pH | 8.5 | 6 – 9 | ✅ Cumple |
| Tensoactivos | 0.8 mg/L | 0.5 mg/L | ⚠️ Requiere dilución o neutralización |
| SST | 150 mg/L | 220 mg/L | ✅ Cumple |

---

## 4. Dimensionamiento del Pre-tratamiento

### 4.1 Lógica del Sistema

Basado en la comparación anterior, el sistema recomienda acciones:

```
SI DQO_efluente > Límite_TULSMA:
    → Recomendar coagulación/floculación + filtración
    → Calcular dosis de coagulante necesaria

SI pH_efluente > 9 o < 6:
    → Recomendar neutralización
    → Calcular volumen de ácido/base necesario

SI Tensoactivos_efluente > Límite_TULSMA:
    → Recomendar filtración con carbón activado
    → O dilución controlada (si el volumen lo permite)
```

### 4.2 Tabla de Recomendaciones por Escenario

| Escenario | Pre-tratamiento Sugerido | Complejidad | Costo Estimado |
|---|---|---|---|
| DQO < 500, pH 6-9 | Solo rejilla de sólidos → vertido seguro | Baja | Mínimo |
| DQO 500-1500, pH 6-9 | Rejilla + coagulación + filtro de arena | Media | Moderado |
| DQO > 1500 | Rejilla + coagulación + filtración + carbón activado | Alta | Mayor |
| pH > 9 | Neutralización con ácido cítrico o CO₂ | Baja-Media | Bajo |
| Alta grasa | Trampa de grasas previa a todo lo anterior | Baja | Bajo |

---

## 5. Métricas del Dashboard

### 5.1 KPIs Propuestos para el Software

| KPI | Fórmula | Unidad |
|---|---|---|
| **Ahorro de producto vs. dosificación manual** | `(Dosis_manual_estimada - Dosis_calculada) / Dosis_manual_estimada × 100` | % |
| **Consumo de agua por m²** | `V_agua / A` | L/m² |
| **Carga contaminante generada** | `DQO_efluente × V_solución` | mg (masa total de contaminante) |
| **Reducción de carga contaminante** | Comparación con escenario sin dosificación óptima | % |
| **Costo por m² limpiado** | `(Costo_producto × V_producto + Costo_agua × V_agua) / A` | USD/m² |
| **Estado de cumplimiento TULSMA** | Semáforo (verde/amarillo/rojo) por parámetro | — |

### 5.2 Estimación de la "Dosificación Manual" para Comparación

Para demostrar el ahorro, el sistema necesita un baseline. La investigación sugiere:

| Parámetro | Dosificación Manual (típica) | Dosificación Optimizada | Diferencia |
|---|---|---|---|
| Producto por m² | 10-20 mL/m² (variable, sin control) | Calculada según fórmulas | -20% a -40% |
| Agua por m² | 0.3-0.8 L/m² (exceso frecuente) | Calculada según proceso | -15% a -30% |
| DQO del efluente | Desconocida | Estimada y verificable | Trazable |

---

## 6. Fichas Técnicas de Productos Biodegradables (Ejemplos)

Para que la calculadora funcione, necesita datos de ficha técnica. Estos son valores típicos que pueden usarse en la simulación:

### 6.1 Detergente Multiusos Biodegradable (Genérico)

| Parámetro | Valor |
|---|---|
| Tipo | Detergente multiusos concentrado |
| Dilución recomendada | 1:50 (2%) para uso general, 1:20 (5%) para suciedad pesada |
| pH (concentrado) | 10.5 – 12.0 |
| Tensoactivos (concentrado) | 15 – 25% |
| DQO (concentrado) | 40.000 – 80.000 mg/L |
| Biodegradabilidad | > 90% en 28 días (OCDE 301B) |
| Presentación | Bidón de 5L, 20L, 200L |

### 6.2 Desengrasante Biodegradable (Genérico)

| Parámetro | Valor |
|---|---|
| Tipo | Desengrasante alcalino concentrado |
| Dilución recomendada | 1:20 (5%) para grasa media, 1:10 (10%) para grasa pesada |
| pH (concentrado) | 12.0 – 13.5 |
| Tensoactivos (concentrado) | 8 – 15% |
| DQO (concentrado) | 60.000 – 120.000 mg/L |
| Biodegradabilidad | > 80% en 28 días |

### 6.3 Desinfectante Biodegradable (Genérico)

| Parámetro | Valor |
|---|---|
| Tipo | Desinfectante cuaternario concentrado |
| Dilución recomendada | 1:100 (1%) para desinfección general |
| pH (concentrado) | 7.0 – 9.0 |
| Principio activo | Cloruro de benzalconio 10% |
| DQO (concentrado) | 20.000 – 40.000 mg/L |

---

## 7. Ejemplo Completo de Simulación

### Escenario: Limpieza de bodega de alimentos — 500 m²

**Datos de entrada:**
- Área: 500 m²
- Superficie: Concreto sellado (Fs = 1.3)
- Suciedad: Media (Fn = 1.0)
- Proceso: Fregado con máquina scrubber (Rh = 0.20 L/m²)
- Producto: Detergente multiusos biodegradable, dilución 1:50 (2%), DQO_p = 50.000 mg/L

**Cálculos:**

```
V_agua     = 500 × 1.3 × 1.0 × 0.20 = 130 Litros
V_producto = 130 × 0.02               = 2.6 Litros
V_solución = 130 + 2.6                = 132.6 Litros

DQO_efluente = (2.6 × 50.000) / 132.6 + 150 = 980 + 150 = 1.130 mg/L

Costo_producto = 2.6 L × $3.50/L              = $9.10
Costo_agua     = 130 L × $0.002/L              = $0.26
Costo_total    = $9.36
Costo_por_m²   = $9.36 / 500                   = $0.019 / m²
```

**Comparación con dosificación manual:**

| Métrica | Manual (estimado) | Optimizado | Ahorro |
|---|---|---|---|
| Producto | 4.0 L | 2.6 L | **35%** |
| Agua | 180 L | 130 L | **28%** |
| DQO efluente | Desconocida | 1.130 mg/L | Ahora es trazable |
| Costo total | ~$14.50 | $9.36 | **35%** |

**Recomendación de pre-tratamiento:**
- DQO (1.130 mg/L) > Límite TULSMA alcantarillado (500 mg/L): ⚠️ **Requiere coagulación + filtración**
- pH estimado (~8.5): ✅ Dentro del rango
- Sugerencia: Rejilla de sólidos + coagulante (sulfato de aluminio 30 mg/L) + filtro de arena

---

## 8. Referencias Técnicas

1. TULSMA — Libro VI, Anexo 1: Norma de calidad ambiental y descarga de efluentes
2. OCDE 301B: Test de biodegradabilidad rápida de productos químicos
3. NSF 350: Estándar para sistemas de reciclaje de agua
4. ISO 14001: Sistemas de gestión ambiental
5. Metcalf & Eddy — *Wastewater Engineering: Treatment and Resource Recovery* (referencia estándar)
6. Fichas técnicas de productos Diversey, Ecolab, Kärcher (valores de referencia)
