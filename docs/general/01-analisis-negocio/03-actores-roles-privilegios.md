# 03. Actores, roles y privilegios

Los roles de cada tipo de negocio están en la carpeta de cada clúster. Aquí solo van los comunes.

## 3.1 Actores de la plataforma (nuestro lado)

| Actor | Descripción |
|-------|-------------|
| **Administrador de plataforma** | Equipo propio. Da de alta organizaciones, activa verticales y publica versiones. No ve datos del cliente sin permiso. |
| **Constructor de la fábrica** | Equipo propio. Crea y mantiene plantillas, paquetes y motores. |
| **Soporte humano** | Acompaña al cliente al armar un negocio y resuelve incidencias. Su acceso a los datos del cliente es temporal y queda registrado. |
| **Asistente IA** | Sistema. Entrevista al cliente, clasifica su negocio y propone la configuración. **No publica nada sin revisión humana.** |

## 3.2 Actores de la organización (lado del cliente)

| Actor | Descripción |
|-------|-------------|
| **Dueño** | Administrador de su organización. Ve todos sus negocios, define objetivos, aprueba, cierra períodos y gestiona usuarios. |
| **Analista / Operador** | Hace el trabajo operativo. Hay N por negocio. Su nombre cambia por vertical: Recepción, Vendedor, Técnico. |
| **Contraparte externa** | Quien paga o recibe el servicio: inquilino, paciente, cliente. Por defecto solo recibe notificaciones. |

## 3.3 Actores de sistema

| Actor | Descripción |
|-------|-------------|
| **Planificador** | Genera obligaciones, evalúa atrasos y envía avisos aunque nadie abra el sistema. |
| **Servicios externos** | Correo, SMS, WhatsApp, proveedor de facturación electrónica y modelos de IA. |

> **Corrección al proceso original:** NUC-P-00 llama al dueño "Superadministrador". Ahora son dos papeles distintos:
> el dueño administra **su** organización y solo el equipo administra la **plataforma**.

## 3.4 Matriz de privilegios del núcleo

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial o configurable

| Funcionalidad | Admin. plataforma | Soporte | Dueño | Analista |
|---------------|:-----:|:-----:|:-----:|:-----:|
| Crear organizaciones | ✅ | ❌ | ❌ | ❌ |
| Publicar plantillas y versiones | ✅ | ❌ | ❌ | ❌ |
| Solicitar un negocio adicional | ❌ | ⚠ en su nombre | ✅ | ❌ |
| Activar la vertical en un negocio | ✅ | ⚠ con revisión | ❌ | ❌ |
| Ajustar configuración del negocio (metas, umbrales) | ❌ | ⚠ acompañado | ✅ | ❌ |
| Gestionar usuarios y cargos de su organización | ❌ | ⚠ acompañado | ✅ | ❌ |
| Ver tablero consolidado | ❌ | ❌ | ✅ | ❌ |
| Ver totales, utilidades, saldos y valorizaciones | ❌ | ❌ | ✅ | ❌ |
| Trabajar la operación diaria | ❌ | ❌ | ✅ | ✅ |
| Aprobar gastos y excepciones | ❌ | ❌ | ✅ | ❌ |
| Asignar tareas a otros colaboradores | ❌ | ❌ | ✅ | ✅ [PREGUNTA [NUC-Q-29](08-preguntas-abiertas.md)] |
| Aprobar el cierre de una tarea | ❌ | ❌ | ✅ | ⚠ solo las que él asignó |
| Cerrar un período | ❌ | ❌ | ✅ | ❌ |
| Ver datos del cliente | ⚠ solo con permiso | ⚠ acceso temporal y auditado | ✅ | ⚠ según rol |
| Consultar la auditoría | ⚠ de plataforma | ❌ | ✅ | ❌ |
| Mensajería interna | ❌ | ❌ | ✅ | ✅ |
