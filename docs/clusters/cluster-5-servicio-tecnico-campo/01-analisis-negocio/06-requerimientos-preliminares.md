# 06. Requerimientos preliminares

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Comunes

| ID | Requerimiento | Prioridad |
|----|---------------|:---------:|
| C5-RF-01 | Bien del cliente con historial de servicios | M |
| C5-RF-02 | OT con flujo de estados configurable | M |
| C5-RF-03 | Ingreso con fotos, estado y firma | M |
| C5-RF-04 | Presupuesto de mano de obra y repuestos | M |
| C5-RF-05 | Aprobación del cliente por enlace | M |
| C5-RF-06 | Asignar técnico y registrar horas | M |
| C5-RF-07 | Reservar y consumir repuestos desde la OT | M |
| C5-RF-08 | Costo y margen por OT, separando mano de obra y repuestos | M |
| C5-RF-09 | Consulta de estado sin cuenta | S |
| C5-RF-10 | Garantías y reclamos vinculados | S |
| C5-RF-11 | Avisos automáticos al cliente | S |
| C5-RF-12 | Margen por técnico | C |

## Por vertical

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C5-RF-20 | Búsqueda por placa, con kilometraje | 5.1 | M |
| C5-RF-21 | Bahías y mecánicos | 5.1 | S |
| C5-RF-22 | Alertas por kilometraje estimado | 5.1 | S |
| C5-RF-23 | Cobro a aseguradoras y clientes en una misma OT | 5.1 | S |
| C5-RF-30 | Ingreso con IMEI o serie, accesorios y contraseña protegida | 5.2 | M |
| C5-RF-31 | Tarifa de diagnóstico descontable | 5.2 | M |
| C5-RF-32 | Control de equipos abandonados | 5.2 | S |
| C5-RF-40 | Contratos de abono con generación de OT | 5.3 | M |
| C5-RF-41 | Planificador de rutas y cuadrillas | 5.3 | S |
| C5-RF-42 | Certificado de servicio con firma digital | 5.3 | M |
| C5-RF-43 | Entrega de insumos, herramientas y uniformes | 5.3 | S |
| C5-RF-44 | Facturación masiva de abonos y extras | 5.3 | M |

## No funcionales propios

| ID | Requerimiento |
|----|---------------|
| C5-RNF-01 | **Trabajo en campo:** app usable en celular y tolerante a mala conexión, con sincronización posterior |
| C5-RNF-02 | Las contraseñas de equipos van cifradas y no aparecen en reportes ni exportaciones |
| C5-RNF-03 | El enlace de consulta o aprobación es único, difícil de adivinar y con vencimiento |
| C5-RNF-04 | Las fotos se comprimen, y conservan fecha y hora |
