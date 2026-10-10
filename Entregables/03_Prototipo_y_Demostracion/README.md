# 📁 03 — Prototipo y Demostración

> **Peso en evaluación: 20%** ⭐ (EL MÁS ALTO)
> **Criterio:** "Prototipo, demo o simulación práctica"

## ⚠️ Importancia

Este criterio es el de **mayor peso** en la evaluación Y es el **primer criterio de desempate**.
El Manual dice: *"La ausencia de desarrollo práctico no implica descalificación automática, pero sí deberá existir una demostración verificable."*

## 📌 Cosas por Hacer (Tareas Pendientes)

### Opción A: Prototipo con Figma + Calculadora (Recomendado Mínimo)

1. **`prototipo_figma_link.md`**
   - Link al prototipo clickeable en Figma
   - Pantallas mínimas:
     - Login / Selección de proyecto
     - Formulario de entrada: área, superficie, suciedad, producto
     - Resultado: dosis calculada (agua + producto)
     - Dashboard con métricas de ahorro
     - Reporte de efluente: DQO estimada vs. límite TULSMA (semáforo)

2. **`calculadora_dosificacion.xlsx`** (o Google Sheets)
   - Hoja de cálculo con las fórmulas de `Investigacion/contexto_tecnico_dosificacion.md`
   - Entrada: área, tipo de superficie, suciedad, producto
   - Salida: volumen de agua, volumen de producto, DQO efluente, costo, semáforo TULSMA
   - **Esta es la "prueba de concepto" matemática de que el sistema funciona**

3. **`video_demo.mp4`**
   - Video de 2-3 minutos mostrando:
     - Navegación por el prototipo Figma
     - Uso de la calculadora con un caso real
     - Interpretación de resultados
   - **Sirve como respaldo si falla la demo en vivo**

### Opción B: App Web Funcional (Mayor Impacto) ⭐⭐⭐⭐⭐

1. **`app_web/`** (carpeta del proyecto)
   - App web funcional generada con **Bolt.new**, **v0.dev** o **Streamlit**
   - Incluye la lógica de cálculo real (no solo UI)
   - Dashboard interactivo con gráficas
   - Link desplegado en la nube (Vercel, Netlify, Streamlit Cloud)

2. **`link_app.md`**
   - URL del deployment
   - Instrucciones de uso

### Opción C: Simulación en Streamlit (Python) ⭐⭐⭐⭐

1. **`app_streamlit.py`**
   - Dashboard interactivo en Python/Streamlit
   - Sliders para área, suciedad, tipo de superficie
   - Gráficas de comparación antes/después
   - Semáforo de cumplimiento TULSMA

### Archivos Complementarios (para todas las opciones):

4. **`evidencia_calculo.md`**
   - Documentación de todas las fórmulas usadas
   - Justificación de los factores (de dónde salen los coeficientes)
   - Referencia a literatura y fichas técnicas

5. **`mockups_ui/`** (carpeta de imágenes)
   - Capturas de las pantallas principales
   - Al menos 4-5 pantallas

## Herramientas Recomendadas

| Herramienta | Esfuerzo | Impacto | Notas |
|---|---|---|---|
| **Figma** (prototipo clickeable) | 4-8 horas | ⭐⭐⭐ | Diseño profesional, interactivo pero no funcional |
| **Google Sheets/Excel** (calculadora) | 2-4 horas | ⭐⭐⭐ | Demuestra que las fórmulas funcionan |
| **Bolt.new** (app web con IA) | 2-6 horas | ⭐⭐⭐⭐⭐ | App funcional desde un prompt, impresiona al jurado |
| **v0.dev** (UI con IA) | 2-4 horas | ⭐⭐⭐⭐ | UI premium generada con IA, componentes React |
| **Streamlit** (dashboard Python) | 4-8 horas | ⭐⭐⭐⭐ | Interactivo con gráficas, fácil si saben Python |
| **Loom / OBS** (video) | 30 min | Respaldo | Siempre tener un video de backup |
