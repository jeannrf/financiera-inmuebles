# 03. Actores, roles y privilegios

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

| Actor | Descripción | Verticales |
|-------|-------------|------------|
| **Dueño / Director** | Ve caja, ingresos y liquidaciones | Todas |
| **Recepción / Caja** | Agenda, cobra y cierra caja | Todas |
| **Profesional** (médico, docente, instructor, veterinario) | Atiende y registra evolución | Todas |
| **Auxiliar / Groomer** | Apoya en la atención | 4.1, 4.4 |
| **Persona atendida / Tutor** | Reserva y recibe recordatorios, con portal opcional | Todas |

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Recepción | Profesional |
|---------------|:-----:|:-----:|:-----:|
| Gestionar toda la agenda | ✅ | ✅ | ⚠ solo la suya |
| Ver datos de contacto | ✅ | ✅ | ✅ |
| Ver y escribir **historia clínica** | ⚠ según rol profesional | ❌ | ✅ a sus pacientes |
| Registrar atención | ✅ | ⚠ marca llegada | ✅ |
| Vender paquetes y cobrar | ✅ | ✅ | ❌ |
| Cerrar caja | ✅ | ✅ propia | ❌ |
| Reabrir una caja cerrada | ✅ | ❌ | ❌ |
| Ver ingresos totales | ✅ | ❌ | ❌ |
| Ver liquidación | ✅ todas | ❌ | ⚠ propia |
| Congelar membresías | ✅ | ⚠ con límite | ❌ |

> **Atención:** en 4.1 tener todos los permisos del negocio no debería bastar para leer una historia clínica. Un dueño sin rol profesional no necesariamente debe tener acceso. Validar con asesoría legal.
