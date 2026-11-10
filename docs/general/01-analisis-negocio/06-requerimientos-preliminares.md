# 06. Requerimientos preliminares del núcleo

> Es un borrador para el SRS general. La prioridad usa **MoSCoW**: **M** (Must), **S** (Should), **C** (Could), **W** (Won't, por ahora no).
> La columna **Etapa** remite a [07-fases-y-alcance.md](07-fases-y-alcance.md).
> Los números originales se conservan con el prefijo `NUC-`.

## 6.1 Requerimientos funcionales

### Provenientes del análisis original

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| NUC-RF-01 | Iniciar sesión con usuario y contraseña | M | 1 |
| NUC-RF-02 | Gestionar usuarios y asignarles un rol (Dueño, Analista; N analistas) | M | 1 |
| NUC-RF-03 | Restringir pantallas y datos según el rol (el analista no ve montos agregados, ganancias ni valorizaciones; ver [NUC-RN-30](05-reglas-de-negocio-y-calculos.md)) | M | 1 |
| NUC-RF-04 | Gestionar **negocios** (N), cada uno con un objetivo mensual | S | 2 |
| NUC-RF-05 | **Tablero** de inicio con una tarjeta por negocio: monto real frente al objetivo, semáforo y acceso al módulo | S | 2 |
| NUC-RF-06 | **Mensajería interna** analista → dueño (por ejemplo, gasto pendiente de aprobación), marcable como leída | S | 2 |
| NUC-RF-07 | Bandeja de **alertas** dentro del sistema | M | 1 |
| NUC-RF-08 | Enviar alertas por **correo electrónico** | M | 1 |
| NUC-RF-09 | Enviar alertas por **SMS** *(sube de C a S: la PPT pide alertas por teléfono como característica macro. Ver [NUC-Q-27](08-preguntas-abiertas.md))* | S | 2–3 |
| NUC-RF-10 | Repositorio de **documentos** (imágenes o PDF) asociados a entidades, consultables por período | M | 1 |
| NUC-RF-11 | Configurar parámetros: días de umbral de alerta, tasas de impuestos, tabla de UIT, tasa de referencia | M | 1–2 |
| NUC-RF-12 | Bitácora de auditoría (quién registró o cambió qué y cuándo) | S | 1 |

### Multi-tenancy y fábrica [EQUIPO]

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| NUC-RF-13 | Aislar los datos por **organización** desde el primer esquema de base de datos | M | 1 |
| NUC-RF-14 | Registrar paquetes y verticales con versión, y activarlos por negocio | M | 1 |
| NUC-RF-15 | Configurar por plantilla: campos adicionales, estados, etiquetas y parámetros por defecto | S | 2 |
| NUC-RF-16 | Administrar organizaciones, negocios y versiones desde un panel interno | S | 2 |
| NUC-RF-17 | Definir los flujos de aprobación por negocio | S | 2 |
| NUC-RF-18 | Cierre de período con condiciones que aporta cada paquete | S | 2 |
| NUC-RF-19 | Acceso de soporte temporal, con permiso del dueño y auditado | S | 2 |
| NUC-RF-20 | Exportar todos los datos de una organización o un negocio | S | 3 |
| NUC-RF-21 | Publicar versiones de plantilla por tandas y revertirlas | C | 3 |
| NUC-RF-22 | Solicitud de negocio adicional con su flujo de propuesta, revisión y aprobación | C | 3 |
| NUC-RF-23 | Asistente IA de entrevista y clasificación, que propone una plantilla para revisión humana | C | 3+ |
| NUC-RF-24 | Facturación de la plataforma: planes, negocios contratados y cobro al cliente | C | 3+ |

### Finanzas y servicios comunes [MAPEO]

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| NUC-RF-30 | Registrar ingresos y egresos con centro de costo | M | 1 |
| NUC-RF-31 | Cuentas por cobrar y cuentas por pagar | M | 1–2 |
| NUC-RF-32 | Cajas y bancos con conciliación de saldos | S | 2 |
| NUC-RF-33 | Estado de Resultados (P&L) mensual y anual por negocio y centro de costo, y **total consolidado** de todos los negocios | S | 2 |
| NUC-RF-34 | Directorio unificado de contactos con uno o más papeles | M | 1 |
| NUC-RF-35 | Plantillas de PDF para contratos, recibos y presupuestos | S | 2 |
| NUC-RF-36 | Motor de estados y tableros Kanban configurables | S | 2 |
| NUC-RF-37 | Calificación de pago de un contacto con criterios configurables | S | 2 |
| NUC-RF-38 | **Comprobantes electrónicos** (boleta y factura) mediante un proveedor autorizado | S | Por definir ([NUC-Q-07](08-preguntas-abiertas.md)) |
| NUC-RF-39 | **Fondos de terceros:** registrar dinero ajeno fuera del P&L hasta aplicarlo o devolverlo | S | 2 |

### Colaboración y tareas [CONFIRMADO — PPT cliente]

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| NUC-RF-40 | **Asignar tareas** a otros colaboradores (título, descripción, responsable, fecha límite, negocio y entidad relacionada) | M | 1–2 |
| NUC-RF-41 | Estados de la tarea (pendiente, en curso, por aprobar, cerrada, rechazada) y notificación al responsable | M | 1–2 |
| NUC-RF-42 | **Aprobación para cerrar una tarea:** el responsable la marca como terminada y quien la asignó (o el dueño) la aprueba o la devuelve, con comentario y evidencia | M | 1–2 |
| NUC-RF-43 | Bandeja "mis tareas" y "tareas que asigné", con alerta de tareas vencidas | S | 2 |
| NUC-RF-44 | **Calculadora** integrada, accesible desde cualquier pantalla ([NUC-Q-30](08-preguntas-abiertas.md)) | C | 2 |
| NUC-RF-45 | **Gráfico de barras de evolución** (ingresos, egresos y resultado por período) por negocio y consolidado | S | 2 |

> **Cambio de alcance:** el motor de tareas e hitos estaba previsto solo como motor activable para el Clúster 3. Con la PPT, la **tarea básica entre colaboradores pasa al núcleo**. Los hitos y dependencias de proyecto siguen en C3.

### Integraciones y futuro (original etapa 3)

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| NUC-RF-80 | Integración con **WhatsApp** (recibir mensajes y comprobantes, enviar recordatorios) *(sube de C a S: la PPT lo pone en la portada; explicar al cliente por qué va en la etapa 3, [CLI-Q-10](../../clientes/cliente-piloto/02-preguntas-abiertas.md))* | S | 3 |
| NUC-RF-81 | Chat o **videollamada** interna *(sube de C a S: la PPT lo pone en la portada; mismo motivo que NUC-RF-80)* | S | 3 |
| NUC-RF-82 | Lectura automática de comprobantes (OCR) que solo **sugiere** monto y fecha | C | 3 |
| NUC-RF-85 | ~~Plantillas para otros rubros~~ → ahora es el centro del producto; ver NUC-RF-14 y NUC-RF-15, y los [clústeres](../../clusters/README.md) | — | — |

## 6.2 Requerimientos no funcionales

| ID | Categoría | Requerimiento |
|----|-----------|---------------|
| NUC-RNF-01 | **Seguridad** | Contraseñas con hash (bcrypt o Argon2); sesiones con expiración; control de acceso por rol aplicado en el **servidor**, no solo en la interfaz |
| NUC-RNF-02 | **Privacidad** | Se guardan datos personales (DNI, copias del DNI, datos laborales, boletas): hay que cumplir la **Ley 29733** de Protección de Datos Personales (consentimiento del inquilino, acceso restringido, archivos no públicos) |
| NUC-RNF-03 | **Integridad** | Los registros históricos son inmutables (NUC-RN-01) y los períodos cerrados se bloquean; queda auditoría de los cambios |
| NUC-RNF-04 | **Disponibilidad y respaldo** | Copias de seguridad automáticas diarias de la base de datos y de los archivos; procedimiento de restauración probado |
| NUC-RNF-05 | **Escalabilidad** | Arquitectura modular: un núcleo común más módulos por negocio; agregar un negocio o rubro no debe requerir rehacer el núcleo. Debe soportar cientos de departamentos sin degradarse |
| NUC-RNF-06 | **Usabilidad** | Interfaz interactiva y sencilla para un usuario no técnico; las tareas frecuentes (registrar pago y voucher) en ≤ 3 pasos; en español; moneda S/ con formato peruano |
| NUC-RNF-07 | **Portabilidad** | **Versión web** accesible desde una laptop (navegador) y usable en el celular (diseño responsivo), para empresas pequeñas. **App de escritorio** con la misma interfaz y el mismo backend, para empresas medianas y grandes [CONFIRMADO — CLI-Q-04, 10/Nov/2026; criterio de tamaño en NUC-Q-31] |
| NUC-RNF-08 | **Rendimiento** | Las pantallas principales cargan en < 2 s con los volúmenes esperados |
| NUC-RNF-09 | **Confiabilidad de alertas** | Las tareas programadas (cuotas, alertas) se ejecutan a diario aunque nadie abra el sistema; los envíos fallidos se reintentan y se registran |
| NUC-RNF-10 | **Precisión** | Los cálculos monetarios usan tipo decimal (nunca coma flotante) y un redondeo definido |
| NUC-RNF-11 | **Mantenibilidad** | Código versionado (Git), pruebas automáticas de los cálculos críticos y documentación |
| NUC-RNF-12 | **Configurabilidad** | Las tasas de impuestos, la UIT, los umbrales y los pesos de la calificación son parámetros, no valores fijos en el código |
| NUC-RNF-13 | **Almacenamiento** | Soporta imágenes y PDF de hasta ~10 MB, organizados por inmueble, inquilino y período |
| NUC-RNF-14 | **Aislamiento** | Las consultas se filtran por organización en una capa que el programador no pueda olvidar, por ejemplo, seguridad a nivel de fila en la base de datos. Debe haber pruebas automáticas de fuga entre organizaciones |
| NUC-RNF-15 | **Extensibilidad** | Añadir un paquete no requiere modificar el núcleo. Las dependencias van del paquete al núcleo, y se comprueban en la integración continua |
| NUC-RNF-16 | **Versionado** | Plantillas y paquetes tienen versión y migraciones reversibles; un negocio sabe en qué versión está |
| NUC-RNF-17 | **Equidad de carga** | Límites por organización para que un cliente grande no degrade a los demás |
| NUC-RNF-18 | **Observabilidad** | Registros, métricas y errores identificados por organización y negocio, sin exponer datos personales |
| NUC-RNF-19 | **Uso de IA** | El uso de datos de clientes en modelos de IA requiere consentimiento y se minimiza; toda propuesta queda registrada junto con quién la aprobó |
| NUC-RNF-20 | **Portabilidad de datos** | El cliente puede obtener sus datos en formato abierto |
| NUC-RNF-21 | **Sensibilidad por paquete** | Un paquete puede declarar datos sensibles (salud, contraseñas de equipos) con cifrado y acceso más estrictos |
| NUC-RNF-22 | **Retención** | La información contable y tributaria (ingresos, egresos, comprobantes, vouchers, reportes) se conserva al menos **10 años** y no se puede eliminar antes de ese plazo, ni siquiera al dar de baja un negocio ([NUC-RN-29](05-reglas-de-negocio-y-calculos.md), [NUC-Q-28](08-preguntas-abiertas.md)) [CONFIRMADO — PPT cliente] |
| NUC-RNF-23 | **Despliegue en servidores** | El sistema se instala en **servidores** (dedicados o propios del cliente) en lugar de la nube pública. El backend se entrega como un paquete instalable por cliente, con respaldos, tareas programadas y envío de correo funcionando en ese servidor ([arquitectura](../04-arquitectura/README.md#modelo-de-despliegue-pedido-por-el-cliente-cli-q-04-respondida-el-10112026)) [CONFIRMADO — CLI-Q-04; detalle en NUC-Q-32] |

## 6.3 Restricciones conocidas


- El equipo tiene experiencia en **desarrollo web** y **SQL**; plazo de unos **2 semestres**, con 3 personas que trabajan los domingos y en su tiempo libre.
- Presupuesto bajo para servicios de pago: hay que elegir proveedores de correo, SMS y hosting con planes gratuitos o baratos.
- La integración con WhatsApp tiene costo y requisitos (API oficial de WhatsApp Business), por eso se deja para la etapa 3.
- Solo el Clúster 1 tiene un cliente real que valide. Los demás clústeres son hipótesis hasta conseguir uno.
