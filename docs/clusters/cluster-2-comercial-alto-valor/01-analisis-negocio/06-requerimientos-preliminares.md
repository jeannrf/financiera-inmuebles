# 06. Requerimientos preliminares

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Comunes

| ID | Requerimiento | Prioridad |
|----|---------------|:---------:|
| C2-RF-01 | Registrar leads, detectar duplicados y asignar responsable | M |
| C2-RF-02 | Pipeline configurable con etapas y probabilidad | M |
| C2-RF-03 | Cotizaciones por líneas con costos, precios y margen | M |
| C2-RF-04 | Versionado de cotizaciones y PDF | M |
| C2-RF-05 | Aprobación de descuentos | S |
| C2-RF-06 | Conversión de una cotización aceptada en contrato o pedido con plan de pagos | M |
| C2-RF-07 | Reglas de comisión por rol y evento (venta o cobro) | M |
| C2-RF-08 | Liquidación de comisiones con aprobación y ajustes | M |
| C2-RF-09 | Forecast frente al objetivo | S |
| C2-RF-10 | Margen real por expediente con costos imputados | M |
| C2-RF-11 | Alertas por oportunidades inactivas | S |
| C2-RF-12 | Reasignar cartera conservando el historial | S |

## Por vertical

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C2-RF-20 | Cartera de pólizas por ramo, aseguradora, bien y coberturas | 2.1 | M |
| C2-RF-21 | Pipeline automático de renovaciones | 2.1 | M |
| C2-RF-22 | Seguimiento de siniestros | 2.1 | S |
| C2-RF-23 | Conciliar comisiones de aseguradoras frente a las cedidas | 2.1 | M |
| C2-RF-24 | Control de primas pendientes | 2.1 | S |
| C2-RF-30 | Inventario unitario de vehículos con costos de alistamiento | 2.2 | M |
| C2-RF-31 | Tasación y retoma como parte de pago | 2.2 | M |
| C2-RF-32 | Trámites de la venta (crédito, seguro, transferencia, placas) | 2.2 | S |
| C2-RF-33 | Consignación con liquidación al dueño | 2.2 | S |
| C2-RF-40 | Presupuestos compuestos con margen objetivo | 2.3 | M |
| C2-RF-41 | Cobro por hitos y desviación presupuestal | 2.3 | M |
| C2-RF-42 | Activar contrato de mantenimiento al finalizar | 2.3 | S |
| C2-RF-50 | Constructor de itinerarios con pasajeros y documentos | 2.4 | M |
| C2-RF-51 | Confirmaciones de proveedores | 2.4 | M |
| C2-RF-52 | Cupos bloqueados en salidas grupales | 2.4 | S |
| C2-RF-53 | Multimoneda y fechas límite de pago | 2.4 | M |

## No funcionales propios

| ID | Requerimiento |
|----|---------------|
| C2-RNF-01 | Los vendedores no pueden exportar la cartera completa; las exportaciones quedan en auditoría |
| C2-RNF-02 | Los documentos de pasajeros (pasaporte, visa) y datos de siniestros de salud tienen acceso restringido |
