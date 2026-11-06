# 08. Preguntas abiertas de la plataforma

> Son preguntas para el **equipo**, a diferencia de las del cliente piloto.
> Las marcadas con ⭐ bloquean el diseño del núcleo.

## Decisiones tomadas

| ID | Decisión | Fecha | Consecuencia |
|----|----------|-------|--------------|
| NUC-Q-01 | El negocio financiero es un **módulo complementario**, no un clúster. Se mantienen 6 clústeres. | 2026-11-06 | Se documenta en [modulos/inversiones-y-liquidez](../../modulos/inversiones-y-liquidez/README.md) |
| NUC-Q-02 | Restaurantes y tiendas **van en el Clúster 6**, porque comparten muchas ventas, proveedores e inventario. Forman la vertical 6.3. | 2026-11-06 | Falta definir si tiendas y restaurantes son una sola plantilla ([C6-Q-30](../../clusters/cluster-6-comercio-distribucion-produccion/01-analisis-negocio/08-preguntas-abiertas.md)) |
| NUC-Q-09 | El producto será de **una empresa propia del equipo**. El cliente piloto es su primer cliente. | 2026-11-06 | Corresponde a la opción (A) de [CLI-Q-03](../../clientes/cliente-piloto/02-preguntas-abiertas.md). Falta comunicárselo al cliente |

## Estructura de la plataforma

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-03 | ¿Cada clúster tendrá su propia arquitectura como sistema separado, o como paquete dentro del mismo código? | Un solo código base con paquetes; el documento de arquitectura de cada clúster registra solo su diferencia. |
| NUC-Q-04 | ¿El aislamiento va por organización, por negocio o ambos? | Datos aislados por organización y permisos por negocio. |

## Modelo comercial

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-05 ⭐ | ¿El dueño crea un negocio por su cuenta (como dice NUC-P-00) o lo solicita con acompañamiento (como en el modelo comercial)? | Solicitado y acompañado al inicio; el autoservicio llega para casos A cuando las plantillas estén maduras. |
| NUC-Q-17 ⭐ | ¿Cuándo se constituye la empresa, quiénes son los socios y en qué proporción? ¿A nombre de quién se firma con el cliente piloto si aún no existe? | Acordarlo por escrito entre los 3 antes de firmar con el cliente; validar con un abogado. |
| NUC-Q-10 | ¿Cómo se cobra: pago inicial, mensualidad por negocio, por usuarios o por volumen? | Implantación + mensualidad por negocio, a validar. |
| NUC-Q-11 | ¿Qué incluye el soporte humano y cuál es su límite? ¿Qué pasa con un caso D? | Definir un catálogo de servicio con precios. |
| NUC-Q-12 | ¿Las mejoras hechas para un cliente quedan disponibles para los demás? | Sí, salvo pacto contrario; debe estar en el contrato. |
| NUC-Q-13 | ¿A qué mercado apuntamos primero, solo Perú? | Solo Perú al inicio; la moneda y los impuestos siguen como parámetros. |

## Cumplimiento y datos

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-06 ⭐ | El proceso de alta busca a la persona "en la base centralizada". ¿Centralizada para una organización o para toda la plataforma? Una lista compartida de morosos entre clientes tiene riesgo legal serio. | Solo por organización. Consultar a un abogado antes de plantear otra cosa. |
| NUC-Q-07 ⭐ | **Comprobantes electrónicos SUNAT:** el mapeo habla de "facturación" en casi todos los clústeres y ningún documento lo aborda. Para C4, C5 y C6 es indispensable. ¿Va en el núcleo? | Servicio del núcleo conectado a un proveedor autorizado, activable por negocio. Validar con un contador. |
| NUC-Q-08 | ¿Qué obligaciones implica custodiar datos de terceros de muchas empresas (Ley 29733) y datos de salud? | Consulta legal antes de vender el primer cliente externo. |
| NUC-Q-14 | ¿Qué datos pueden enviarse a un proveedor de IA y con qué consentimiento? | Por defecto, solo la descripción del negocio y nunca datos de sus clientes. |

## Núcleo

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-15 | ¿Se necesita contabilidad formal o basta con un P&L de gestión? | P&L de gestión; no reemplaza al sistema contable. |
| NUC-Q-16 | ¿Multimoneda en el núcleo? C2 (viajes) e Inversiones la necesitan. | Sí, por negocio y con tipo de cambio registrado en cada operación. |
| NUC-Q-26 | En el tablero, ¿qué representa el "monto" de cada negocio: ingresos del mes, acumulado anual o patrimonio? ¿Cómo se define el objetivo? | Que lo defina cada paquete; validar con el cliente piloto para C1 e Inversiones. |
