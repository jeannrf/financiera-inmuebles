# 03. Actores, roles y privilegios

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

| Actor | Descripción | Verticales |
|-------|-------------|------------|
| **Dueño / Gerente comercial** | Ve el pipeline, márgenes y comisiones. Aprueba descuentos | Todas |
| **Vendedor / Ejecutivo** | Lleva sus oportunidades y cotizaciones | Todas |
| **Sub-agente / Bróker externo** | Vende por comisión; ve solo su cartera | 2.1 |
| **Administrativo / Trámites** | Gestiona documentos, cobros y plazos | Todas |
| **Técnico de levantamiento** | Visita y dimensiona | 2.3 |
| **Tasador** | Valoriza vehículos de retoma | 2.2 |
| **Cliente** | Recibe cotizaciones; sin acceso en un inicio | Todas |
| **Terceros** | Aseguradora, banco, notaría, proveedores; sin acceso | Según vertical |

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Vendedor | Sub-agente | Administrativo |
|---------------|:-----:|:-----:|:-----:|:-----:|
| Ver todo el pipeline | ✅ | ⚠ solo el suyo | ⚠ solo el suyo | 👁 |
| Crear y editar cotizaciones | ✅ | ✅ | ✅ | ❌ |
| Aprobar descuentos sobre el límite | ✅ | ❌ | ❌ | ❌ |
| Ver costo y margen de la cotización | ✅ | ⚠ configurable | ❌ | ⚠ |
| Reasignar cartera | ✅ | ❌ | ❌ | ❌ |
| Ver comisiones | ✅ todas | ⚠ propias | ⚠ propias | 👁 |
| Aprobar liquidaciones de comisión | ✅ | ❌ | ❌ | ❌ |
| Registrar pagos | ✅ | ❌ | ❌ | ✅ |
| Ver forecast global | ✅ | ❌ | ❌ | ❌ |
