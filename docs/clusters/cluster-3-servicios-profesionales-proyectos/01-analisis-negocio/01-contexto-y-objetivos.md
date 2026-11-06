# 01. Contexto y objetivos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 1.1 Perfil del negocio

Empresas que **venden conocimiento, tiempo o entregables**, con proyectos cerrados o igualas mensuales. Su costo principal es la hora de su gente.
Sus preguntas de fondo son **¿qué cliente o proyecto me deja dinero?, ¿qué se vence?, ¿qué puedo cobrar ya?**

## 1.2 Problema común [INFERIDO]

- Nadie registra las horas, y por eso no se sabe si un cliente es rentable.
- Una iguala puede terminar costando más de lo que paga, sin que se note.
- El dinero que pasa por el negocio a nombre del cliente (tasas, pauta publicitaria) distorsiona los resultados.
- Se pierden vencimientos, con consecuencias legales o tributarias.
- Trabajo adicional que no se cobra porque no se aprobó ni se registró.
- En obra: lo gastado frente a lo presupuestado se conoce al final, cuando ya no hay remedio.

## 1.3 Objetivos

| ID | Objetivo | Verticales |
|----|----------|------------|
| OE-C3-01 | Medir la **rentabilidad por proyecto y por cliente** | Todas |
| OE-C3-02 | Gestionar igualas y proyectos cerrados en un mismo sistema | 3.1, 3.2 |
| OE-C3-03 | Cobrar por hitos, avance o etapas sin olvidar ninguno | Todas |
| OE-C3-04 | Separar dinero de terceros de los ingresos propios | 3.1, 3.2 |
| OE-C3-05 | Asegurar el cumplimiento de plazos y vencimientos | 3.1 |
| OE-C3-06 | Comparar presupuesto y gasto real por partida | 3.3 |
| OE-C3-07 | Controlar el adicional antes de ejecutarlo | 3.2, 3.3 |

## 1.4 Qué usa de la plataforma

| Motor | Importancia | Uso aquí |
|-------|:-----------:|----------|
| Finanzas, Caja y P&L | Crítico | Centro de costo por proyecto |
| Gestión de Tareas / Hitos | Crítico | Es el corazón del clúster |
| Contratos y Cobro Recurrente | Alto | Igualas (**ya lo construye el piloto**) |
| CRM y Pipelines | Alto | Venta del servicio, pipeline de candidatos |
| Liquidación de Comisiones | Medio | Reclutadores, freelancers |
| Agenda, Turnos y Calendario | Bajo | Audiencias, reuniones |
| Inventario y Catálogo | Bajo | Materiales de obra, sin Kardex completo al inicio |
