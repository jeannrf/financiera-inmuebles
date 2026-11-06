# 06. Requerimientos preliminares

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Comunes

| ID | Requerimiento | Prioridad |
|----|---------------|:---------:|
| C4-RF-01 | Agenda por profesional y recurso, sin choques | M |
| C4-RF-02 | Estados de cita y lista de espera | M |
| C4-RF-03 | Recordatorios automáticos | M |
| C4-RF-04 | Paquetes con saldo y movimientos | M |
| C4-RF-05 | Membresías con renovación | M |
| C4-RF-06 | Caja diaria por método de pago con cierre | M |
| C4-RF-07 | Ingresos diferidos y su reconocimiento | S |
| C4-RF-08 | Liquidación de honorarios con reglas | M |
| C4-RF-09 | Historial por persona atendida | M |
| C4-RF-10 | Portal para que el cliente reserve | S |
| C4-RF-11 | Venta de mostrador con descuento de stock | S |
| C4-RF-12 | Indicadores: ocupación, inasistencias | S |

## Por vertical

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C4-RF-20 | Historia clínica evolutiva con acceso restringido | 4.1 | M |
| C4-RF-21 | Odontograma o esquema corporal | 4.1 | S |
| C4-RF-22 | Consentimientos firmados y fotos de antes y después | 4.1 | M |
| C4-RF-23 | Presupuestos financiados en cuotas | 4.1 | S |
| C4-RF-30 | Ciclos, cursos, niveles, horarios, aulas y profesores | 4.2 | M |
| C4-RF-31 | Matrícula con control de cupo y asistencia | 4.2 | M |
| C4-RF-32 | Pensiones con descuentos y control de morosos | 4.2 | M |
| C4-RF-33 | Clases particulares por bolsa de horas | 4.2 | S |
| C4-RF-40 | Clases grupales con cupo y reserva de lugar | 4.3 | M |
| C4-RF-41 | Planes y pases, con congelamiento | 4.3 | M |
| C4-RF-42 | Métricas de MRR y churn | 4.3 | S |
| C4-RF-50 | Propietario con N mascotas y su ficha | 4.4 | M |
| C4-RF-51 | Recordatorios de medicina preventiva | 4.4 | M |
| C4-RF-52 | Agendas separadas de consultorio y peluquería | 4.4 | S |
| C4-RF-53 | Internaciones | 4.4 | C |
| C4-RF-54 | Ticket único de servicios y productos | 4.4 | M |

## No funcionales propios

| ID | Requerimiento |
|----|---------------|
| C4-RNF-01 | **Datos de salud:** cifrado, acceso por rol profesional y auditoría de cada lectura (Ley 29733; normativa de historia clínica a validar) |
| C4-RNF-02 | Reservar y marcar asistencia desde el celular en menos de 3 toques |
| C4-RNF-03 | La agenda se mantiene consistente con varias personas reservando a la vez |
| C4-RNF-04 | Enviar recordatorios a tiempo; el costo de mensajes se controla por negocio |
