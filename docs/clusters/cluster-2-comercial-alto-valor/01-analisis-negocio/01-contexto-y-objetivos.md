# 01. Contexto y objetivos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 1.1 Perfil del negocio

Negocios con ventas **consultivas de ticket medio o alto**: cada cierre toma semanas, pasa por cotizaciones negociadas e involucra comisiones.
Sus preguntas de fondo son **¿cuánto voy a cerrar este mes?, ¿cuánto gano realmente en cada venta?, ¿a quién le debo comisión?**

La diferencia con el Clúster 6: aquí importa cada expediente individual y no el volumen.

## 1.2 Problema común [INFERIDO]

- Los leads y su seguimiento viven en WhatsApp y en la memoria del vendedor; si se va, se lleva la cartera.
- Se pierde la versión de la cotización que el cliente aceptó.
- La proyección de ingresos es una intuición.
- Las comisiones se calculan a mano y generan disputas.
- El margen real de cada venta se conoce tarde o nunca, porque los costos llegan después.
- Se olvidan renovaciones, que son el ingreso más barato de conseguir.

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C2-01 | Ver todo el pipeline y que la cartera pertenezca a la empresa | Todas |
| OE-C2-02 | Versionar las cotizaciones y saber cuál se aceptó | Todas |
| OE-C2-03 | Proyectar ingresos según la probabilidad de cierre | Todas |
| OE-C2-04 | Cobrar en cuotas o hitos con control de saldos | Todas |
| OE-C2-05 | Calcular comisiones de forma automática y transparente | Todas |
| OE-C2-06 | Conocer el margen real por expediente | Todas |
| OE-C2-07 | No perder renovaciones | 2.1, 2.3 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | Margen por expediente, CxC en cuotas |
| CRM y Pipelines | Crítico | Es el corazón del clúster |
| Liquidación de Comisiones | Crítico | Vendedores, brókers y sub-agentes |
| Contratos y Cobro Recurrente | Medio | Planes de pago, renovaciones |
| Agenda, Turnos y Calendario | Medio | Visitas, levantamientos, salidas |
| Gestión de Tareas / Hitos | Medio | Trámites por expediente |
| Inventario y Catálogo | Bajo | Solo vehículos (inventario unitario) |
