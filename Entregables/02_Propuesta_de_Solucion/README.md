# 📁 02 — Propuesta de Solución

> **Peso en evaluación: 15%**
> **Criterio:** "Innovación de la solución"

## 📌 Cosas por Hacer (Tareas Pendientes)

### 📋 Entregables por Realizar:

1. **`propuesta_general.md`**
   - Descripción completa de la solución en 3 etapas:
     1. **Dosificación Algorítmica:** Software que calcula dosis exacta según m², superficie, suciedad y producto
     2. **Monitoreo y Trazabilidad:** Registro de consumo por jornada, área y operario
     3. **Pre-tratamiento de Efluentes:** Estimación automática de carga contaminante y recomendación de tratamiento
   - El nombre propuesto: "Sistema Tecnológico Integral de Dosificación Inteligente y Gestión Circular de Efluentes"

2. **`diagrama_de_flujo.png`** (CRÍTICO)
   - Diagrama visual del proceso completo:
     ```
     [Entrada de datos] → [Cálculo de dosis] → [Dispensación] → [Limpieza]
                                                                     ↓
     [Dashboard] ← [Registro de consumo] ← [Recolección agua gris]
                                                                     ↓
     [Reporte TULSMA] ← [Estimación DQO/pH] ← [Pre-tratamiento]
     ```
   - Herramienta: draw.io, Lucidchart, Figma

3. **`diferenciador_vs_competencia.md`**
   - Usar la tabla comparativa de la sección 8 de `Investigacion/investigacion_soluciones_existentes.md`
   - Mostrar que Diversey, Ecolab, Kärcher etc. solo cubren partes del problema
   - Nuestro diferenciador: **integración digital dosificación → efluente**

4. **`arquitectura_tecnica.md`**
   - Stack: Frontend (React/Angular), Backend (Node.js/.NET), Base de datos
   - Diagrama de componentes del software
   - Si se menciona hardware futuro: ESP32/Arduino + sensor de flujo + electroválvula

## Preguntas que el jurado buscará responder

- ¿La solución es realmente innovadora o es más de lo mismo?
- ¿Cómo se diferencia de lo que ya existe?
- ¿La lógica de funcionamiento es clara y convincente?
