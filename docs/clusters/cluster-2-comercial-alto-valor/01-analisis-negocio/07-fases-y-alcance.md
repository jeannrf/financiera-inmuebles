# 07. Fases y alcance

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

**Dependencias que deben existir antes:** el núcleo y los motores **CRM y Pipelines** y **Comisiones**. Ninguno lo construye el piloto en su totalidad.

**Vertical de entrada sugerida: 2.1 Seguros** [INFERIDO]. Su renovación recurrente reutiliza alertas y cobro, y no necesita inventario. La decisión final depende del primer cliente.

| Fase | Contenido |
|------|-----------|
| **MVP del clúster** | Leads, pipeline, cotización versionada, cierre, plan de pagos, comisiones simples, margen por expediente |
| **Vertical de entrada** | Pólizas, renovaciones, conciliación de comisiones |
| **Ampliación** | Forecast, aprobaciones, siniestros |
| **Otras verticales** | 2.3 (presupuesto compuesto, hitos) · 2.2 (inventario unitario, retoma) · 2.4 (multimoneda, cupos) |

**Fuera de alcance inicial:**

- Cotizadores conectados en línea a aseguradoras.
- Conexión con sistemas de reserva aérea (GDS) y motores de reserva en línea.
- Generar leads o gestionar campañas de publicidad.
- Trámites automáticos ante registros públicos.
