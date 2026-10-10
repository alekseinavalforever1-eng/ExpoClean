# 📋 Guía Maestra de Entregables — Hackathon Expo Clean 2026 (Reto 4)

> **Reto:** Optimización y neutralización del impacto ambiental en el uso de agua y vertido de residuos químicos.
> **Área Estratégica:** Sostenibilidad y Economía Circular

---

## ⚠️ Contexto del Evento

| Fecha | Actividad |
|---|---|
| 8 de octubre 2026 | Capacitación previa (obligatoria) |
| 16 de octubre 2026 | Jornada de desarrollo (Día 1) |
| 17 de octubre 2026 | Validación, pitch y evaluación (Día 2) |

---

## 🏗️ Estructura de Carpetas y Entregables

Cada carpeta corresponde a una sección de la **Guía de Trabajo (Anexo 5)** del Manual del Hackathon y a los **criterios de la Matriz de Evaluación (Anexo 6)**.

---

### 📁 `01_Comprension_del_Problema/` — Peso en evaluación: **15%**

> **Criterio evaluado:** "Comprensión del problema"
> 
> El jurado evalúa si el equipo entiende con claridad el problema real, a quién afecta y qué evidencia tiene.

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `problema_definicion.md` | Redacción formal: qué ocurre, dónde, a quién afecta, consecuencia principal. | Markdown o PDF | Cualquier editor de texto |
| `evidencia_del_problema.md` | **Datos duros** que demuestren que el problema existe: estadísticas, papers, reportes de la industria. | Markdown con fuentes | Investigación web / papers |
| `mapa_de_actores.png` | Diagrama visual de stakeholders (empresas de limpieza → clientes → medio ambiente → regulador). | Imagen / Diagrama | Figma, Canva, Miro, draw.io |
| `contexto_regulatorio.md` | Resumen del TULSMA (Libro VI, Anexo 1) y normativa ecuatoriana de efluentes. | Markdown | Ver carpeta `Investigacion/` |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Qué problema estamos resolviendo?
- ¿A quién afecta?
- ¿Qué evidencia tenemos?

---

### 📁 `02_Propuesta_de_Solucion/` — Peso en evaluación: **15% (Innovación)**

> **Criterio evaluado:** "Innovación de la solución"
> 
> El jurado evalúa qué proponen, cómo funciona y qué la diferencia de lo que ya existe.

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `propuesta_general.md` | Descripción completa de la solución de 3 etapas (Dosificación → Monitoreo → Pre-tratamiento). | Markdown o PDF | Editor de texto |
| `diagrama_de_flujo.png` | Diagrama del proceso completo: entrada de agua/químico → dosificación → limpieza → captura de agua gris → filtrado/neutralización. | Imagen SVG/PNG | draw.io, Lucidchart, Figma |
| `diferenciador_vs_competencia.md` | Tabla comparativa de la solución propuesta vs. competidores existentes (Diversey, Ecolab, Kärcher, etc.). | Markdown con tabla | Ver `Investigacion/investigacion_soluciones_existentes.md` |
| `arquitectura_tecnica.md` | Stack tecnológico propuesto: frontend, backend, sensores (si aplica), flujo de datos. | Markdown con diagrama | draw.io |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Qué proponemos?
- ¿Cómo funciona?
- ¿Qué la hace diferente?

---

### 📁 `03_Prototipo_y_Demostracion/` — Peso en evaluación: **20%** ⭐

> **Criterio evaluado:** "Prototipo, demo o simulación práctica"
> 
> **Este es el criterio con mayor peso.** El jurado busca que hayas construido algo demostrable, no solo teoría.

| Entregable | Descripción | Formato Sugerido | Herramienta Recomendada |
|---|---|---|---|
| `prototipo_app/` | Prototipo interactivo (clickeable) de la app/software de dosificación y dashboard. | Link a Figma o app web | **Figma** (prototipo clickeable) o **Bolt.new / v0.dev** (app funcional generada con IA) |
| `simulacion_proceso/` | Simulación del flujo completo: cálculo de dosis → resultado → parámetros de efluente. | Hoja de cálculo interactiva o web app | **Google Sheets / Excel con fórmulas** o **Streamlit (Python)** |
| `video_demo.mp4` | Video corto (2–3 min) mostrando el prototipo funcionando. Sirve como respaldo si falla la demo en vivo. | Video MP4 | Grabación de pantalla (OBS, Loom) |
| `evidencia_calculo.md` | Documentación de las fórmulas y lógica de dosificación (balance de materia). | Markdown con ecuaciones | LaTeX / Markdown |
| `mockups_ui/` | Capturas o diseños de las pantallas principales del software. | Imágenes PNG | Figma, Canva |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Qué construimos?
- ¿Qué parte es funcional?
- ¿Qué evidencia presentamos?

#### 💡 Cómo presentar un "prototipo" sin construir hardware real

El Manual dice explícitamente: *"La ausencia de desarrollo práctico no implica descalificación automática cuando el reto no permita un prototipo físico en 48 horas, pero sí deberá existir una demostración verificable."*

Opciones viables:

| Opción | Esfuerzo | Impacto ante el jurado |
|---|---|---|
| **Figma interactivo** con flujo completo de la app | Medio | ⭐⭐⭐ |
| **App web funcional** generada con Bolt.new o v0.dev | Medio-Alto | ⭐⭐⭐⭐⭐ |
| **Google Sheets/Excel** con calculadora de dosificación parametrizada | Bajo | ⭐⭐⭐ |
| **Streamlit (Python)** con dashboard interactivo de métricas | Medio | ⭐⭐⭐⭐ |
| **Video del concepto** animado (Canva / PowerPoint) | Bajo | ⭐⭐ |

> **Recomendación:** Combinar **Figma** (para el diseño de la app) + **Google Sheets** (para la calculadora de dosificación con fórmulas reales de balance de materia) + **video de respaldo**. Si el equipo tiene capacidad técnica, usar **Bolt.new** o **v0.dev** para generar una web app funcional en horas.

---

### 📁 `04_Validacion/` — Peso en evaluación: implícito en varios criterios

> **Criterio evaluado:** Se evalúa transversalmente en "Comprensión del problema" e "Impacto potencial"

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `validacion_tecnica.md` | Resultados de pruebas de concepto: ¿funciona el cálculo? ¿los parámetros de efluente coinciden con la literatura? | Markdown | Pruebas con la simulación |
| `feedback_usuarios.md` | Si se logra consultar a alguien del sector (ej. BAQ, empresa de limpieza), documentar sus comentarios. | Markdown | Entrevista informal |
| `comparacion_antes_despues.md` | Tabla comparativa: escenario actual (dosificación al ojo) vs. escenario con la solución. Con números. | Markdown con tabla | Datos de la simulación |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Qué probamos?
- ¿Con quién?
- ¿Qué modificamos?

---

### 📁 `05_Viabilidad/` — Peso en evaluación: **15%**

> **Criterio evaluado:** "Viabilidad técnica"

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `viabilidad_tecnica.md` | Análisis de factibilidad: ¿se puede implementar con tecnología disponible? ¿Qué se necesita? | Markdown | Investigación |
| `recursos_necesarios.md` | Lista de recursos para ir del prototipo a la realidad: hardware, software, certificaciones, aliados. | Markdown con tabla | — |
| `riesgos_y_mitigacion.md` | Identificación de riesgos técnicos, operativos y de mercado con plan de mitigación. | Markdown con tabla | — |
| `roadmap_implementacion.png` | Línea de tiempo visual de las 3 etapas de implementación. | Imagen | Figma, Canva, Miro |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Cómo se implementaría?
- ¿Qué recursos requiere?
- ¿Qué riesgos existen?

---

### 📁 `06_Modelo_de_Negocio/` — Peso en evaluación: **10% (calidad de presentación)**

> **Criterio evaluado:** Indirectamente en la presentación y pitch

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `modelo_canvas.png` | Business Model Canvas de una página. | Imagen | Canva, Miro, Strategyzer |
| `propuesta_de_valor.md` | ¿Quién es el cliente? ¿Cuál es la propuesta de valor? ¿Cómo genera ingresos? | Markdown | — |
| `costos_principales.md` | Estructura de costos estimada para el MVP y para la operación. | Markdown con tabla | — |

**Qué debe responder esta carpeta** (según Anexo 5):
- ¿Quién es el cliente o beneficiario?
- ¿Cuál es la propuesta de valor?
- ¿Cómo genera ingresos o sostenibilidad?
- ¿Cuáles son los costos principales?

---

### 📁 `07_Pitch_Final/` — Peso en evaluación: **10% (calidad presentación) + 10% (proceso/equipo)**

> **Criterio evaluado:** "Calidad de la presentación" + "Proceso y trabajo en equipo"

| Entregable | Descripción | Formato Sugerido | Herramienta |
|---|---|---|---|
| `pitch_deck.pptx` o `.pdf` | Presentación del pitch (7-10 slides). | PowerPoint / Canva PDF | Canva, Google Slides, PowerPoint |
| `guion_pitch.md` | Script de lo que dice cada persona del equipo, con tiempos. | Markdown | — |
| `demo_backup.mp4` | Video de respaldo del demo por si falla la conexión. | Video MP4 | OBS, Loom |

**Estructura del pitch** (según Anexo 5, sección 5.7):
1. Problema
2. Solución
3. Prototipo / demo
4. Impacto
5. Viabilidad
6. Modelo de negocio
7. Próximo paso

---

### 📁 `08_Documentacion_Administrativa/`

> Documentación que se requiere si resultan ganadores (Anexo 9 del Manual).

| Documento | Cuándo se necesita |
|---|---|
| Ficha de identificación del equipo | Al ganar |
| Copias de documentos de identidad | Al ganar |
| Designación de representante | Al ganar |
| Ficha técnica y versión final del proyecto | Al ganar |
| Declaración de autoría y originalidad | Al ganar |
| Declaración de aceptación del premio | Al ganar |
| Datos bancarios | Al ganar |

> **Nota:** Esta documentación NO se presenta durante el Hackathon. Solo se requiere si el equipo gana. Pero es bueno tenerla lista.

---

## 📊 Resumen: Matriz Oficial de Evaluación (Anexo 6)

| # | Criterio | Peso | Carpeta principal |
|---|---|---|---|
| 1 | Comprensión del problema | **15%** | `01_Comprension_del_Problema/` |
| 2 | Innovación de la solución | **15%** | `02_Propuesta_de_Solucion/` |
| 3 | Prototipo, demo o simulación práctica | **20%** | `03_Prototipo_y_Demostracion/` ⭐ |
| 4 | Impacto potencial | **15%** | `04_Validacion/` + `01_Comprension/` |
| 5 | Viabilidad técnica | **15%** | `05_Viabilidad/` |
| 6 | Calidad de la presentación | **10%** | `07_Pitch_Final/` |
| 7 | Proceso y trabajo en equipo | **10%** | `07_Pitch_Final/` |

> **Desempate:** Si hay empate en puntaje final, se desempata en este orden: Prototipo (20%) → Impacto (15%) → Viabilidad (15%) → Innovación (15%) → Comprensión (15%) → Presentación (10%) → Proceso (10%).

---

## 🔧 Herramientas Recomendadas (Sin Construir Hardware Real)

### Para el Prototipo / MVP

| Herramienta | Tipo | Para qué usarla | Costo |
|---|---|---|---|
| **Figma** | Diseño UI/Prototipo | Crear el diseño interactivo clickeable de la app de dosificación | Gratis (plan starter) |
| **Bolt.new** | Generador de apps con IA | Generar una web app funcional a partir de un prompt de texto | Gratis (limitado) |
| **v0.dev** (Vercel) | Generador de UI con IA | Generar componentes React de UI premium con un prompt | Gratis (limitado) |
| **Streamlit** | Framework Python para dashboards | Crear un dashboard interactivo con métricas de dosificación y ahorro | Gratis |
| **Google Sheets / Excel** | Hoja de cálculo | Calculadora de dosificación paramétrica con fórmulas reales | Gratis |

### Para la Presentación

| Herramienta | Para qué usarla |
|---|---|
| **Canva** | Pitch deck, Business Model Canvas, infografías |
| **draw.io / diagrams.net** | Diagramas de flujo del proceso de limpieza |
| **Miro** | Mapas de actores, journey maps |
| **Loom / OBS Studio** | Grabación de video demo de respaldo |
| **Google Slides** | Alternativa a PowerPoint para el pitch |

### Para la Investigación

| Herramienta | Para qué usarla |
|---|---|
| **Google Scholar** | Buscar papers académicos |
| **ScienceDirect / MDPI** | Papers sobre tratamiento de aguas y dosificación |
| **ResearchGate** | Papers y preprints de investigación |

---

## 📁 Carpeta `Investigacion/`

Contiene la investigación profunda que respalda toda la propuesta:

| Archivo | Contenido |
|---|---|
| `investigacion_soluciones_existentes.md` | Análisis general de productos, tecnologías, papers y campañas que ya abordan esta problemática en el mundo |
| `investigacion_profunda_fichas_y_contactos.md` | Fichas técnicas detalladas (SmartDose, Ecolab, SEKO, Hydro Systems, Tennant), enlaces oficiales TDS/SDS, contactos locales en Ecuador y plantillas de correo listas para enviar |
| `contexto_tecnico_dosificacion.md` | Fundamentación técnica sobre dosificación inteligente, balance de materia, y tratamiento de aguas grises |

---

## ✅ Checklist Rápido Pre-Hackathon

- [ ] Carpeta `01_Comprension_del_Problema/` → Problema documentado con evidencia
- [ ] Carpeta `02_Propuesta_de_Solucion/` → Diagrama de flujo + diferenciador
- [ ] Carpeta `03_Prototipo_y_Demostracion/` → Al menos Figma + calculadora
- [ ] Carpeta `04_Validacion/` → Antes/después con números
- [ ] Carpeta `05_Viabilidad/` → Roadmap + riesgos
- [ ] Carpeta `06_Modelo_de_Negocio/` → Canvas + propuesta de valor
- [ ] Carpeta `07_Pitch_Final/` → Deck + guion + video backup
- [ ] Carpeta `Investigacion/` → Investigación respaldando todo
