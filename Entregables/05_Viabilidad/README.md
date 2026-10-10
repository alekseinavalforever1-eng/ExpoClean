# 📁 05 — Viabilidad

> **Peso en evaluación: 15%**
> **Criterio:** "Viabilidad técnica"

## 📌 Cosas por Hacer (Tareas Pendientes)

1. **`viabilidad_tecnica.md`**
   - ¿Se puede implementar con tecnología disponible? **Sí.** Las fórmulas son algebra básica. La app es software estándar. Los sensores (futuro) son componentes de bajo costo.
   - ¿Qué es factible en las 48h del hackathon? Software de cálculo + dashboard
   - ¿Qué requiere desarrollo adicional? Hardware de dispensación automática, integración IoT

2. **`recursos_necesarios.md`**
   - Tabla de recursos por fase:

   | Fase | Recurso | Costo Estimado | Prioridad |
   |---|---|---|---|
   | **MVP (Hackathon)** | Desarrollo web app | $0 (trabajo del equipo) | Alta |
   | **Piloto** | Servidor cloud | $20-50/mes | Alta |
   | **Piloto** | Acceso a empresa aliada para pruebas | Gestión (FEDELIMP) | Alta |
   | **Hardware v1** | ESP32 + sensor de flujo + electroválvula | $50-100 por unidad | Media |
   | **Escalamiento** | Certificación ARCA para reúso de agua | Variable | Media |
   | **Escalamiento** | Desarrollo de módulo de pre-filtrado físico | $500-2000 | Baja (fase posterior) |

3. **`riesgos_y_mitigacion.md`**
   - Tabla de riesgos:

   | Riesgo | Probabilidad | Impacto | Mitigación |
   |---|---|---|---|
   | Datos de fichas técnicas incompletos | Media | Alto | Crear base de datos colaborativa con FEDELIMP |
   | Resistencia al cambio de operarios | Alta | Medio | Interfaz simple, capacitación mínima |
   | Variabilidad real de la suciedad vs. modelo | Media | Medio | Calibración con datos reales en piloto |
   | Regulación cambiante (TULSMA) | Baja | Medio | Parámetros actualizables en software |
   | Competencia de grandes fabricantes | Media | Alto | Enfoque en PYMES LATAM, modelo SaaS accesible |

4. **`roadmap_implementacion.png`** (o `.pdf`)
   - Línea de tiempo visual:
     - **Mes 0-1:** MVP validado en hackathon → Piloto con 1 empresa
     - **Mes 1-3:** Programa de Aceleración → Calibración con datos reales
     - **Mes 3-6:** Hardware v1 → Integración IoT
     - **Mes 6-12:** Escalamiento B2B → Suscripción a empresas FEDELIMP
   - Herramienta: Canva, Figma, Miro

## Preguntas que el jurado buscará responder

- ¿Es técnicamente factible o es ciencia ficción?
- ¿El equipo sabe qué necesita para llegar a la realidad?
- ¿Han pensado en los riesgos y cómo enfrentarlos?
