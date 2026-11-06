# 01. Contexto y objetivos

## 1.1 Perfil del negocio

Negocios que ganan dinero **cediendo el uso temporal de un bien** bajo contrato: un departamento, un auto, una excavadora, un
escritorio o una bodega. Sus preguntas de fondo son **¿está ocupado?, ¿me pagaron?, ¿cuánto me rinde cada unidad?**

Es el clúster de **origen** de la plataforma: su vertical inmobiliaria definió buena parte del núcleo.

## 1.2 Problema común

- El cobro recurrente se controla a mano, en Excel y WhatsApp.
- Se descubre tarde quién no pagó y a veces nadie avisa.
- Comprobantes y contratos dispersos, sin expediente para acciones legales.
- No se sabe cuánto rinde cada unidad descontando sus gastos.
- Gastos compartidos difíciles de repartir sin perder dinero.

El caso real y sus citas están en [el cliente piloto](../../../clientes/cliente-piloto/01-contexto-y-compromisos.md).

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C1-01 | Generar cobros recurrentes y alertar vencimientos y morosidad sin intervención | Todas |
| OE-C1-02 | Archivar comprobantes y documentos por contraparte, unidad y período | Todas |
| OE-C1-03 | Conocer la **rentabilidad por unidad** con su centro de costo | Todas |
| OE-C1-04 | Repartir gastos comunes con cuadre exacto | 1.1 y 1.2 |
| OE-C1-05 | Mantener el historial y la calificación de cada contraparte | Todas |
| OE-C1-06 | Controlar la disponibilidad y la ocupación de cada unidad | Todas |
| OE-C1-07 | Valorizar los inmuebles y comparar su retorno con otras opciones | 1.1 |
| OE-C1-08 | Controlar garantías y estado del bien al entregar y devolver | 1.3 y 1.4 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | Centro de costo por unidad |
| Contratos y Cobro Recurrente | Crítico | Es el corazón del clúster |
| CRM y Pipelines | Alto | Comercialización (1.1) |
| Liquidación de Comisiones | Alto | Agentes y liquidación a propietarios (1.1) |
| Agenda, Turnos y Calendario | Medio | Ocupación, reservas de SUM, salas |
| Gestión de Tareas / Hitos | Bajo | Tickets de mantenimiento |
| Inventario y Catálogo | Nulo | No aplica |

## 1.5 Propuesta de valor por vertical

| Vertical | Lo que más valora |
|----------|-------------------|
| 1.1 Inmobiliarias | Cobranza sin perseguir a nadie y saber cuánto rinde cada inmueble |
| 1.2 Edificios | Recibos mensuales exactos y morosidad transparente |
| 1.3 Rent-a-car y flotas | Disponibilidad, actas de entrega y ROI por unidad |
| 1.4 Coworking y storage | Facturación recurrente automática y consumo de créditos |
