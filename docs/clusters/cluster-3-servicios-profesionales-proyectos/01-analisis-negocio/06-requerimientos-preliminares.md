# 06. Requerimientos preliminares

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Comunes

| ID | Requerimiento | Prioridad |
|----|---------------|:---------:|
| C3-RF-01 | Cuentas de cliente y proyectos con responsables | M |
| C3-RF-02 | Contratos de iguala con obligación mensual y entregables | M |
| C3-RF-03 | Hitos con monto, fecha, aprobación y cobro | M |
| C3-RF-04 | Tareas con asignación y estado | M |
| C3-RF-05 | Registro de horas con costo hora vigente | M |
| C3-RF-06 | Gastos propios y por cuenta del cliente | M |
| C3-RF-07 | Rentabilidad por proyecto y por cliente | M |
| C3-RF-08 | Compartir entregables con el cliente | S |
| C3-RF-09 | Alertas de vencimientos y de hitos no facturados | M |
| C3-RF-10 | Asignar freelancers con pago por tarea | S |

## Por vertical

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C3-RF-20 | Expedientes con línea de tiempo de actuaciones | 3.1 | M |
| C3-RF-21 | Calendario de vencimientos procesales y tributarios | 3.1 | M |
| C3-RF-22 | Cobro por etapas o por éxito | 3.1 | S |
| C3-RF-30 | Entregables mensuales comprometidos | 3.2 | M |
| C3-RF-31 | Sprints o fases con aprobación del cliente | 3.2 | S |
| C3-RF-32 | Separar pauta publicitaria y fee | 3.2 | M |
| C3-RF-40 | Presupuesto por partidas y rubros, con versión aprobada | 3.3 | M |
| C3-RF-41 | Avance físico por partida | 3.3 | M |
| C3-RF-42 | Certificaciones con retenciones | 3.3 | M |
| C3-RF-43 | Adicionales con aprobación | 3.3 | M |
| C3-RF-44 | Órdenes de compra y destajos por partida | 3.3 | M |
| C3-RF-45 | Flujo de caja por obra, presupuesto frente a real | 3.3 | M |
| C3-RF-84 | **Presupuestos de remodelación por m²** (material + mano de obra), pedido por el cliente piloto | 3.3 | C |
| C3-RF-50 | Vacantes por empresa cliente | 3.4 | M |
| C3-RF-51 | Pipeline de candidatos por vacante | 3.4 | M |
| C3-RF-52 | Facturación escalonada sobre salario anual | 3.4 | M |
| C3-RF-53 | Seguimiento de la garantía del candidato | 3.4 | S |

## No funcionales propios

| ID | Requerimiento |
|----|---------------|
| C3-RNF-01 | Acceso a expedientes solo por asignación, con auditoría de consultas (3.1) |
| C3-RNF-02 | Registrar avance y fotos desde el celular en obra, tolerando mala conexión (3.3) |
| C3-RNF-03 | Datos de candidatos con consentimiento y plazo de conservación (3.4; Ley 29733) |
