# 01. Contexto y objetivos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 1.1 Perfil del negocio

Negocios de atención al público que **monetizan bloques de tiempo** de un profesional o de un espacio, y venden sesiones, paquetes o membresías.
Sus preguntas de fondo son **¿tengo la agenda llena?, ¿cuánto entró hoy a caja?, ¿cuánto le debo a cada profesional?, ¿quién dejó de venir?**

## 1.2 Problema común [INFERIDO]

- La agenda vive en un cuaderno o en WhatsApp, con choques y horas vacías.
- Las inasistencias se pierden sin aviso previo.
- Los paquetes se llevan a mano: nadie sabe cuántas sesiones le quedan a alguien.
- Se cuenta como ingreso del mes el dinero de sesiones aún no prestadas.
- Las comisiones de los profesionales se calculan a mano al fin de mes.
- No se detectan las bajas hasta que ya es tarde.

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C4-01 | Llenar la agenda sin choques entre profesionales ni recursos | Todas |
| OE-C4-02 | Reducir inasistencias con recordatorios | Todas |
| OE-C4-03 | Controlar el saldo de paquetes y membresías | Todas |
| OE-C4-04 | Separar el dinero cobrado del ingreso ganado | Todas |
| OE-C4-05 | Cerrar la caja diaria por método de pago | Todas |
| OE-C4-06 | Liquidar honorarios de forma automática | 4.1, 4.2 |
| OE-C4-07 | Mantener el historial de cada persona | 4.1, 4.4 |
| OE-C4-08 | Medir retención y MRR | 4.2, 4.3 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | Caja diaria, ingresos diferidos |
| Agenda, Turnos y Calendario | Crítico | Es el corazón del clúster |
| Contratos y Cobro Recurrente | Alto | Membresías y pensiones (**ya lo construye el piloto**) |
| Liquidación de Comisiones | Alto | Honorarios de profesionales y docentes |
| Inventario y Catálogo | Medio | Insumos y mostrador |
| CRM y Pipelines | Bajo | Captación básica |
| Gestión de Tareas / Hitos | Bajo | No es central |

> **Lo que este clúster agrega a la plataforma:** el primer motor de agenda, un **portal externo** (el cliente final reserva) y datos sensibles de salud.
