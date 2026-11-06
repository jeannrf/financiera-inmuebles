# 01. Contexto y objetivos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 1.1 Perfil del negocio

Negocios que **reparan o mantienen un bien que ya es del cliente**, en local o a domicilio. La unidad de trabajo es la **Orden de Trabajo (OT)**.
Sus preguntas de fondo son **¿en qué estado está cada trabajo?, ¿cuánto gané en esta OT?, ¿qué trabajo se aprobó?**

La diferencia con el Clúster 1: aquí el bien es **del cliente**. Allá, del negocio.

## 1.2 Problema común [INFERIDO]

- Reclamos por daños que "ya tenía", porque no se documentó el estado de ingreso.
- Trabajos hechos sin aprobación que luego el cliente no quiere pagar.
- Los repuestos se compran y no se cargan a la OT, de modo que el margen es desconocido.
- Los clientes llaman todo el tiempo para preguntar el estado.
- No hay historial del bien ni aviso del próximo mantenimiento.
- Equipos abandonados que ocupan espacio.

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C5-01 | Documentar el estado del bien al ingresar | 5.1, 5.2 |
| OE-C5-02 | Tener aprobación del cliente antes de ejecutar | 5.1, 5.2 |
| OE-C5-03 | Costear cada OT, separando mano de obra y repuestos | Todas |
| OE-C5-04 | Dar visibilidad del estado al cliente sin que llame | 5.1, 5.2 |
| OE-C5-05 | Conservar el historial del bien y anticipar mantenimientos | 5.1, 5.2 |
| OE-C5-06 | Gestionar contratos de abono, rutas y cuadrillas | 5.3 |
| OE-C5-07 | Controlar garantías de reparación | 5.1, 5.2 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | Costeo por OT |
| Agenda, Turnos y Calendario | Alto | Bahías, técnicos, rutas |
| Gestión de Tareas / Hitos | Alto | Flujo de la OT |
| Inventario y Catálogo | Alto | Repuestos e insumos |
| CRM y Pipelines | Medio | Presupuestos |
| Contratos y Cobro Recurrente | Medio | Abonos (**ya lo construye el piloto**) |
| Liquidación de Comisiones | Medio | Comisión por técnico |

> **Lo que este clúster agrega:** trabajo **en campo** desde el celular, firma digital y consulta de estado por parte del cliente.
