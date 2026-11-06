# 04. Procesos de negocio del núcleo

Estos procesos aplican a cualquier negocio. Los operativos de cada rubro están en la carpeta de su clúster.
La numeración de los procesos del documento original se conserva con el prefijo `NUC-`.

Procesos particulares: [C1-P-01 a C1-P-11](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/04-procesos-de-negocio.md) e [INV-P-12](../../modulos/inversiones-y-liquidez/01-analisis-negocio/04-procesos-de-negocio.md).

---

## Parametrización y fábrica

### NUC-P-00. Alta y parametrización de un nuevo negocio (Motor SaaS Multi-tenant)
**AS-IS:** Crear un nuevo negocio requiere estructurar hojas de Excel independientes y redefinir procesos de cobro y registro desde cero.
**TO-BE:**
1. El **Dueño** (Superadministrador) crea una nueva unidad dentro de la plataforma (ej. *Negocio Inmobiliario*, *Negocio Financiero* o *Negocio 3*).
2. Asigna la plantilla de metadatos o el **módulo vertical** correspondiente (Clúster de Activos/Alquileres, Clúster Financiero o Clúster de Proyectos/Construcción).
3. Establece la moneda base, la meta u objetivo de facturación/rendimiento mensual y las reglas de alertas.
4. El sistema aprovisiona el espacio aisladamente (*multi-tenancy*), dejando el nuevo negocio disponible de inmediato en el tablero principal.

> **Ajuste pendiente de confirmar:** este proceso describe al dueño creando el negocio por su cuenta. En el modelo
> comercial, el negocio adicional se **solicita y se paga** con acompañamiento. NUC-P-00 queda entonces como el paso
> técnico de aprovisionamiento, y lo comercial está en NUC-P-16. [NUC-Q-05](08-preguntas-abiertas.md)

### NUC-P-15. Adaptación a nuevos rubros (ej. Construcción / Servicios) mediante la "Fábrica Secreta"
**AS-IS:** Reescribir código o crear sistemas independientes para abordar nuevos modelos de negocio.
**TO-BE:**
1. Cuando el cliente abre un negocio en un nuevo rubro (ej. Construcción con presupuestos por m² o Servicios Técnicos), el desarrollador/administrador **no altera el Core**.
2. En la fábrica interna de metadatos se define el esquema de entidades de la nueva vertical (ej. *Partida de Obra*, *Costo por m²*, *Avance Físico*) y se vinculan a las reglas universales de cobro, usuarios RBAC y tablero.
3. El sistema expone la nueva vertical en el panel multi-tenant como si fuera una aplicación construida a medida, garantizando la mantenibilidad sobre un único código base (*Single Codebase*).

> **Precisión:** esto se cumple sin tocar el núcleo. En un clúster nuevo sí habrá código, pero en un paquete aparte
> ([qué es metadato y qué es código](02-dominio-nucleo.md#23-qué-es-metadato-y-qué-es-código)).

### NUC-P-16. Solicitud y venta de un negocio adicional [EQUIPO]
**AS-IS:** no existe; cada negocio nuevo sería un proyecto aparte.
**TO-BE:**
1. El **Dueño** solicita un nuevo negocio desde la plataforma o por su contacto comercial.
2. El **Asistente IA** lo entrevista: qué vende, a quién, cómo cobra, qué controla hoy y con qué archivos.
3. La IA clasifica el negocio ([árbol de decisión](10-mapa-de-clusters-y-reutilizacion.md#102-cómo-clasificar-un-negocio-nuevo)) y propone clúster, vertical, campos y diferencias.
4. **Soporte humano** revisa la propuesta y la marca como caso A, B, C o D ([modelo comercial](01-vision-y-modelo-de-negocio.md#13-modelo-comercial-equipo)).
5. El **Dueño** recibe alcance, precio y plazo, y aprueba.
6. El **Constructor** prepara lo que falte y deja una plantilla de prueba con datos de ejemplo.
7. El **Dueño** valida; se migran sus datos, se ejecuta NUC-P-00 y el negocio aparece en su tablero.

### NUC-P-17. Actualización de plantillas y paquetes sin romper clientes [INFERIDO]
1. El **Constructor** publica una nueva versión de una plantilla o paquete y sus pruebas pasan.
2. Se aplica primero a un negocio de prueba y luego a los clientes por tandas.
3. Los negocios existentes conservan su versión hasta recibir la migración; sus datos y personalizaciones se preservan.
4. Si algo falla, se revierte a la versión anterior sin afectar a otros negocios.

### NUC-P-18. Salida de un cliente y exportación de datos [INFERIDO]
1. El **Dueño** solicita la baja de un negocio o de toda su organización.
2. El sistema genera una exportación completa de datos y documentos.
3. Tras el plazo acordado, se conserva lo que obliga la ley y se elimina el resto, dejando constancia.

---

## Gobernanza, tablero y notificaciones

### NUC-P-13. Monitoreo del Dashboard Corporativo y Mensajería Auditada
**AS-IS:** Desconexión entre la salud financiera global de los negocios y gestión de mensajes en WhatsApp personal.
**TO-BE:**
1. Al iniciar sesión, el **Dueño** accede al **Dashboard Central (Holding View)**. Visualiza una tarjeta por cada negocio activo (Inmobiliario, Financiero, etc.).
2. Cada tarjeta compara el **Monto Actual cobrado/rendido vs. Objetivo del mes**, pintándose en **Verde** (saludable) o **Rojo** (desviación / morosidad crítica).
3. Los **Analistas** ven un panel exclusivamente operativo donde se ocultan por RBAC los totales recaudados, utilidades, saldos bancarios y valorizaciones.
4. El sistema incluye un canal de **mensajería interna auditada** entre el dueño y los analistas anclado a entidades del sistema (ej. observaciones sobre la cuota del Depto 401), eliminando la dispersión de información en WhatsApp.


### NUC-P-14. Engine central de notificaciones automáticas
**AS-IS:** Tareas mecánicas manuales para enviar avisos de pago, recibos y saludos.
**TO-BE:**
1. El motor programado del Core ejecuta tareas automatizadas para:
   * Emitir recordatorios preventivos de cobro a inquilinos antes del vencimiento.
   * Enviar los recibos desglosados de servicios prorrateados por correo electrónico.
   * Enviar correos institucionales de saludo de **cumpleaños** al inquilino.
   * Notificar al Dueño y Analista sobre renovaciones de contrato próximas a vencer (30-60 días antes).
