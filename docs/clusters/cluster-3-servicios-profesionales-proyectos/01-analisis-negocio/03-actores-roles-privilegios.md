# 03. Actores, roles y privilegios

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

| Actor | Descripción | Verticales |
|-------|-------------|------------|
| **Socio / Dueño** | Ve rentabilidad, aprueba y fija tarifas | Todas |
| **Jefe de proyecto / Residente de obra** | Controla plazos, tareas, costos y avance | Todas |
| **Profesional / Especialista** | Hace las tareas y registra horas | 3.1, 3.2, 3.4 |
| **Freelancer / Subcontratista** | Trabaja por tarea; ve solo lo asignado | 3.2, 3.3 |
| **Administración** | Factura, cobra y paga | Todas |
| **Cliente** | Recibe y aprueba entregables, con portal opcional | Todas |
| **Candidato** | Persona evaluada, sin acceso | 3.4 |

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Socio | Jefe de proyecto | Profesional | Administración |
|---------------|:-----:|:-----:|:-----:|:-----:|
| Crear proyectos e igualas | ✅ | ⚠ proyectos | ❌ | ⚠ |
| Registrar horas | ✅ | ✅ | ⚠ propias | ❌ |
| Ver costo hora de otras personas | ✅ | ❌ | ❌ | ⚠ |
| Ver rentabilidad de su proyecto | ✅ | ⚠ configurable | ❌ | 👁 |
| Ver rentabilidad global | ✅ | ❌ | ❌ | ❌ |
| Aprobar hitos, certificaciones y adicionales | ✅ | ⚠ propone | ❌ | ❌ |
| Registrar gastos reembolsables | ✅ | ✅ | ✅ | ✅ |
| Facturar y cobrar | ✅ | ❌ | ❌ | ✅ |
| Ver expedientes de otros clientes | ✅ | ⚠ asignados | ⚠ asignados | ⚠ |

> **Confidencialidad:** en 3.1 los expedientes pueden estar bajo secreto profesional; en 3.4 hay datos personales de candidatos. Por eso el acceso por defecto es solo a lo asignado.
