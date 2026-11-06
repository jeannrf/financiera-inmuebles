# 01. Contexto y objetivos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 1.1 Perfil del negocio

Negocios de **compraventa de bienes físicos**, donde el stock, los precios y el crédito son el centro. Incluye el caso de "muchas ventas" que
motivó la plataforma, como ferreterías y restaurantes.
Sus preguntas de fondo son **¿cuánto tengo?, ¿cuánto gano realmente?, ¿quién me debe?, ¿qué tengo que reponer?**

**Es el clúster más distinto al piloto:** muchas transacciones pequeñas por día, frente a pocas cuotas al mes.

## 1.2 Problema común [INFERIDO]

- El stock del sistema no coincide con el real (mermas, robos, errores).
- No se conoce el margen por producto, porque el costo cambia con cada compra.
- Se sigue vendiendo a clientes que ya deben.
- Vencimientos que no se ven hasta que la mercadería se pierde.
- Se paga comisión por ventas que nunca se cobraron.
- En fabricación a pedido: cotizaciones hechas a mano y costos reales desconocidos.
- En restaurantes: no se sabe cuánto cuesta realmente cada plato.

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C6-01 | Mantener el stock exacto y trazable en un Kardex | Todas |
| OE-C6-02 | Conocer el costo de lo vendido y el margen en tiempo real | Todas |
| OE-C6-03 | Controlar el crédito y la antigüedad de saldos | 6.1, 6.2 |
| OE-C6-04 | Tomar pedidos con la lista de precios correcta | 6.1 |
| OE-C6-05 | Controlar despachos y devoluciones | 6.1 |
| OE-C6-06 | Pasar de una venta configurada a su producción | 6.2 |
| OE-C6-07 | Vender rápido en caja, con cierre por turno | 6.3 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | CMV, antigüedad de saldos |
| Inventario y Catálogo | Crítico | Es el corazón del clúster (**el piloto no lo construye**) |
| Liquidación de Comisiones | Alto | Sobre lo cobrado |
| CRM y Pipelines | Medio | Pedidos a medida, seguimiento |
| Gestión de Tareas / Hitos | Medio | Producción |
| Contratos y Cobro Recurrente | Bajo | Casi no aplica |
| Agenda, Turnos y Calendario | Bajo | Entregas e instalación |

> **Lo que este clúster agrega:** el motor de inventario, punto de venta rápido, **alto volumen de transacciones** y uso obligatorio de comprobantes electrónicos.
