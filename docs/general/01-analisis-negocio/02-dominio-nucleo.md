# 02. Dominio del núcleo

## 2.1 Las 5 capas

Toda funcionalidad de la plataforma pertenece a **una sola** de estas capas. Es la regla para decidir dónde
se documenta y dónde se programa algo.

| Capa | Qué contiene | ¿Quién la usa? | Forma | Dónde se documenta |
|------|--------------|----------------|-------|--------------------|
| **1. Núcleo** | Clientes, usuarios y roles, directorio, finanzas y tesorería, documentos, estados y alertas, notificaciones, tablero, auditoría y cierre | Todos, siempre activo | Código | `general/` |
| **2. Motores** | Cobro recurrente, CRM y pipelines, agenda, tareas e hitos, inventario, comisiones | Se activan por clúster | Código | `general/`, con su especificación propia |
| **3. Paquete de clúster** | Entidades y lógica compartidas por los negocios del clúster | Los negocios de ese clúster | Código | `clusters/cluster-N/` |
| **4. Plantilla de vertical** | Campos, estados, textos, reportes y parámetros por defecto de un rubro | Los negocios de esa vertical | Metadatos | `clusters/cluster-N/`, sección de la vertical |
| **5. Configuración del negocio** | Moneda, metas, umbrales, usuarios y sus cargos | Un negocio de un cliente | Datos | `clientes/` |

> **Ajuste respecto al mapeo original:** el mapeo pone 4 módulos en el "Núcleo Base", pero su matriz lista 7 módulos.
> La diferencia son los **motores**: su importancia varía entre "Crítico" y "Nulo" según el clúster, así que no
> conviene cargarlos a todos los negocios. [INFERIDO]

Texto original del mapeo:

> **Núcleo Base Compartido (Core Engine)**
> Todos los verticales descritos a continuación heredan automáticamente los siguientes módulos transversales:
> * **Finanzas y Tesorería:** Registro de ingresos y egresos, cuentas por cobrar (CxC), cuentas por pagar (CxP), conciliación de saldos en bancos/cajas y Estado de Resultados (P&L) mensual/anual con centros de costos.
> * **Directorio Unificado:** Gestión de contactos (Clientes, Proveedores, Empleados/Agentes, Aliados).
> * **Gestor Documental y Plantillas:** Generación de contratos/presupuestos en PDF y almacenamiento de archivos adjuntos por entidad.
> * **Motor de Estados y Alertas:** Flujos de trabajo (Kanban/Pipelines) y notificaciones de vencimientos.

## 2.2 Jerarquía de datos

```
Plataforma
└── Organización (el cliente que nos paga; aquí está el aislamiento multi-tenant)
    ├── Usuarios y cargos
    ├── Tablero consolidado (Holding View)
    └── Negocio (N por organización)
        ├── Vertical activada + versión de plantilla
        ├── Moneda base, objetivo mensual, reglas de alerta
        └── Datos operativos (unidades, contratos, pedidos, citas…)
```

- **Organización** es la frontera de seguridad: lo que hay en una jamás se ve desde otra.
- **Negocio** es la frontera operativa: un analista puede trabajar en un negocio y no ver los demás.
- El proceso original habla de "unidad" y de espacio aislado por negocio. Aquí se distinguen los dos niveles porque
  el tablero consolidado necesita cruzar negocios de un mismo dueño. [INFERIDO → [NUC-Q-04](08-preguntas-abiertas.md)]

## 2.3 Qué es metadato y qué es código

El proceso de la fábrica plantea crear verticales "sin alterar el código fuente". Eso se cumple para una parte del
trabajo, no para todo. El límite real es este:

| Se resuelve con **metadatos** (plantilla) | Requiere **código** (paquete o motor) |
|-------------------------------------------|---------------------------------------|
| Campos adicionales de una ficha | Cálculos con reglas propias (prorrateo, indexación UIT, costo promedio) |
| Estados y etapas de un flujo | Movimientos con invariantes (Kardex, caja, saldos de paquete) |
| Roles y visibilidad de campos | Disponibilidad y choques de agenda |
| Textos, etiquetas y vocabulario ("Inquilino", "Paciente") | Integraciones externas (facturación electrónica, WhatsApp) |
| Reportes sobre datos existentes | Trabajo sin conexión o punto de venta rápido |
| Plantillas de PDF y correos | Reglas que exigen coherencia transaccional |
| Tiempos y canales de alertas | |

> **Consecuencia:** la promesa correcta es "**nunca se toca el núcleo**", y no "nunca se escribe código". Un negocio
> de un clúster nuevo lleva código, pero se añade en un paquete aparte. Esto también justifica que cada clúster tenga
> su propio SRS, modelado y arquitectura, que documentan **solo lo que agregan** al núcleo.

## 2.4 Entidades genéricas del núcleo [INFERIDO]

| Entidad | Descripción | Ejemplos por clúster |
|---------|-------------|----------------------|
| **Organización** | Cliente de la plataforma | "Grupo Pérez" |
| **Negocio** | Unidad gestionada, con objetivo mensual | Inmobiliaria, Clínica |
| **Usuario / Cargo / Permiso** | Control de acceso por rol | Dueño, Analista, Recepción |
| **Contacto** | Directorio único con uno o más papeles | Inquilino, Paciente, Proveedor, Empleado |
| **Obligación** | Lo que un contacto debe pagar o se le debe pagar, con vencimiento | Cuota, pensión, factura, certificación |
| **Pago / Comprobante** | Dinero recibido o entregado y su evidencia | Voucher de Yape, cierre de caja |
| **Cuenta y Movimiento** | Caja y bancos, ingresos y egresos | Caja chica, cuenta corriente |
| **Centro de costo** | A qué se imputa un ingreso o gasto para el P&L | Depto 402, Excavadora CAT-01, Proyecto X |
| **Fondo de terceros** | Dinero que pasa por el negocio sin ser ingreso suyo | Garantía (C1), prima (C2), gasto suplido y pauta (C3) |
| **Documento** | Archivo asociado a cualquier entidad | DNI, contrato, foto |
| **Flujo / Estado** | Máquina de estados configurable | Pipeline, Kanban |
| **Alerta / Notificación** | Avisos internos y externos programados | Vencimiento, cumpleaños |
| **Solicitud de aprobación** | Acción que requiere autorización | Gasto de mantenimiento, descuento |
| **Tarea** | Trabajo asignado a un colaborador, con responsable, fecha límite y aprobación de cierre | "Subir el voucher del Depto 401", "Revisar el recibo de luz" |
| **Período** | Mes contable con candado | Octubre 2026 cerrado |
| **Mensaje** | Mensajería interna anclada a una entidad | Observación sobre la cuota del Depto 401 |
| **Registro de auditoría** | Quién hizo qué y cuándo | |

## 2.5 Qué aporta el piloto al núcleo

El Clúster 1 y el módulo de inversiones se analizaron primero, así que varias piezas nacieron con vocabulario
inmobiliario. Este es el camino para generalizarlas:

| Lo que pidió el piloto | Se generaliza como | Capa | Lo usan también |
|------------------------|--------------------|------|-----------------|
| Cuota mensual automática | Obligación recurrente | Motor de cobro recurrente | C3 (igualas), C4 (pensiones), C5 (abonos) |
| Historial de montos e incrementos programados | Precio con fecha de vigencia | Motor de cobro recurrente | C3, C4, C5 |
| Voucher y verificación | Comprobante con política de verificación | Núcleo | Todos, con variación ([ver reglas](05-reglas-de-negocio-y-calculos.md#52-cómo-cambia-cada-regla-según-el-clúster)) |
| Semáforo del inquilino | Calificación de pago del contacto | Núcleo | C4 (alumnos morosos), C6 (línea de crédito) |
| Alerta al dueño por atraso | Escalamiento de alertas | Núcleo | Todos |
| Aprobación de gastos | Flujo de aprobación | Núcleo | C2 (descuentos), C5 (presupuestos) |
| Cierre de mes | Candado de período con condiciones que aporta cada paquete | Núcleo | Todos |
| Tablero de negocios | Holding View con indicador por negocio | Núcleo | Todos |
| ~~Dossier de desalojo~~ | Expediente legal | **Descartado** (13/Nov/2026): el piloto gestiona los desalojos fuera del sistema | Se reconsidera solo si otro cliente lo pide |
| Prorrateo por submedidores | No se generaliza | Paquete C1 | Vertical 1.2 |
| Valorización por UIT | No se generaliza | Paquete C1 (inmuebles) | Requiere análisis para maquinaria o flotas |

## 2.6 Puntos de extensión que debe ofrecer el núcleo [INFERIDO]

Son la forma en que un paquete se conecta sin modificar el núcleo:

1. **Registro de paquete:** cada paquete declara sus entidades, permisos, menús y versión.
2. **Campos configurables** en las entidades del núcleo.
3. **Condiciones de cierre:** cada paquete aporta lo que debe cumplirse para cerrar un período.
4. **Indicador del tablero:** cada paquete define qué es "monto actual" frente al objetivo.
5. **Eventos:** "pago verificado" o "contrato vencido", a los que otros módulos pueden suscribirse.
6. **Tareas programadas** registradas por paquete y ejecutadas por el planificador del núcleo.
7. **Generadores de obligaciones** (cuota, certificación, pensión) que alimentan un mismo flujo de cobro.
