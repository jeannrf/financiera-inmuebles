# 03. Actores, roles y privilegios

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

| Actor | Descripción | Verticales |
|-------|-------------|------------|
| **Dueño / Jefe de taller** | Ve márgenes, aprueba y supervisa | Todas |
| **Recepción / Asesor de servicio** | Recibe el bien, presupuesta y coordina con el cliente | 5.1, 5.2 |
| **Técnico / Mecánico** | Diagnostica y ejecuta | Todas |
| **Almacén** | Entrega repuestos o insumos | Todas |
| **Supervisor de cuadrilla** | Coordina rutas y personal | 5.3 |
| **Cliente** | Aprueba y consulta su estado | Todas |
| **Aseguradora** | Autoriza y paga siniestros, sin acceso | 5.1 |

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Recepción | Técnico | Almacén |
|---------------|:-----:|:-----:|:-----:|:-----:|
| Crear OT | ✅ | ✅ | ⚠ en campo | ❌ |
| Registrar diagnóstico | ✅ | 👁 | ✅ | ❌ |
| Armar y enviar presupuesto | ✅ | ✅ | ⚠ propone | ❌ |
| Ver costo y margen | ✅ | ⚠ configurable | ❌ | ❌ |
| Consumir repuestos | ✅ | ❌ | ⚠ solicita | ✅ |
| Ver contraseña del equipo (5.2) | ⚠ auditado | ❌ | ⚠ asignado y auditado | ❌ |
| Cobrar y entregar | ✅ | ✅ | ⚠ en campo | ❌ |
| Ver margen por técnico | ✅ | ❌ | ❌ | ❌ |
