# 07. Fases y alcance

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

**Dependencias:** núcleo y motores de **Tareas**, **Agenda** e **Inventario**. Son tres motores nuevos respecto del piloto, de modo que conviene llegar aquí después de C3 o C4, que construyen parte de ellos.

**Vertical de entrada sugerida: 5.2 Electrónica y TI** [INFERIDO]: un flujo de OT claro, con la operación en mostrador (sin requerir trabajo en campo al inicio). **5.3** requiere la app de campo y **5.1** tiene mayor volumen de repuestos.

| Fase | Contenido |
|------|-----------|
| **MVP del clúster** | OT, ingreso, presupuesto, aprobación, costeo y cobro |
| **Vertical de entrada** | Serie, contraseña, diagnóstico, consulta de estado y garantía |
| **Ampliación** | Inventario de repuestos, avisos automáticos |
| **Otras verticales** | 5.1 (placa, km, seguros) · 5.3 (abonos, rutas, certificados) |

**Fuera de alcance inicial:**

- Lectura automática de placas o escáneres de diagnóstico.
- Optimización matemática de rutas o rastreo GPS.
- Catálogos de autopartes de fabricantes.
- Conexión en línea con aseguradoras.
