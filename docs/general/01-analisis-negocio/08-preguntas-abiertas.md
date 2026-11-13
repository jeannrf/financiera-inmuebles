# 08. Preguntas abiertas de la plataforma

> Son preguntas para el **equipo**, a diferencia de las del cliente piloto.
> Las marcadas con ⭐ bloquean el diseño del núcleo.

## Decisiones tomadas

| ID | Decisión | Fecha | Consecuencia |
|----|----------|-------|--------------|
| NUC-Q-01 | El negocio financiero es un **módulo complementario**, no un clúster. Se mantienen 6 clústeres. | 2026-11-06 | Se documenta en [modulos/inversiones-y-liquidez](../../modulos/inversiones-y-liquidez/README.md) |
| NUC-Q-02 | Restaurantes y tiendas **van en el Clúster 6**, porque comparten muchas ventas, proveedores e inventario. Forman la vertical 6.3. | 2026-11-06 | Falta definir si tiendas y restaurantes son una sola plantilla ([C6-Q-30](../../clusters/cluster-6-comercio-distribucion-produccion/01-analisis-negocio/08-preguntas-abiertas.md)) |
| NUC-Q-09 | El producto será de **una empresa propia del equipo**. El cliente piloto es su primer cliente. | 2026-11-06 | Corresponde a la opción (A) de [CLI-Q-03](../../clientes/cliente-piloto/02-preguntas-abiertas.md). Falta comunicárselo al cliente |
| NUC-Q-06 | La búsqueda de personas por documento (la "base centralizada" del alta de inquilino) se limita a **cada organización**. No se comparte morosidad entre clientes. | 2026-11-13 | Confirmado por el cliente piloto al conciliar C1-P-02. [NUC-RN-21](05-reglas-de-negocio-y-calculos.md) pasa a confirmada |

## Estructura de la plataforma

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-03 | ¿Cada clúster tendrá su propia arquitectura como sistema separado, o como paquete dentro del mismo código? | Un solo código base con paquetes; el documento de arquitectura de cada clúster registra solo su diferencia. |
| NUC-Q-04 | ¿El aislamiento va por organización, por negocio o ambos? | Datos aislados por organización y permisos por negocio. |

## Despliegue (tras la respuesta del cliente a CLI-Q-04, 10/Nov/2026)

El cliente pidió **web para empresas pequeñas**, **escritorio para medianas y grandes** y **servidores en vez de la nube**
([arquitectura](../04-arquitectura/README.md#modelo-de-despliegue-pedido-por-el-cliente-cli-q-04-respondida-el-10112026)).

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-31 ⭐ | ¿Qué hace que una empresa sea "pequeña" (web) o "mediana/grande" (escritorio)? ¿Usuarios, unidades, sedes, facturación? ¿Una empresa puede pasar de una forma a la otra sin migrar datos? | Criterio por número de usuarios y sedes; la app de escritorio usa el mismo backend, así que cambiar de forma no exige migrar datos. |
| NUC-Q-32 ⭐ | "Servidores en vez de la nube": ¿servidores **propios del cliente** o **dedicados** operados por el equipo? ¿Qué le preocupa de la nube (costo, confianza, control de datos)? ¿Quién hace respaldos y actualizaciones en un servidor del cliente? | Servidor dedicado operado por el equipo para pequeñas; servidor propio o dedicado exclusivo para medianas y grandes, con contrato de soporte que incluya respaldos y actualizaciones. |
| NUC-Q-33 | ¿El cliente piloto (1 analista, 11 unidades) usa la versión web? ¿La app de escritorio entra en alguna de las 3 etapas? | Web para el piloto; escritorio después de la etapa 2, cuando haya un cliente mediano. |

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
| ~~NUC-Q-06~~ | ~~¿Base centralizada por organización o para toda la plataforma?~~ 🟢 **Decidida (13/Nov/2026):** solo por organización. Ver [decisiones tomadas](#decisiones-tomadas). | — |
| NUC-Q-07 ⭐ | **Comprobantes electrónicos SUNAT:** el mapeo habla de "facturación" en casi todos los clústeres y ningún documento lo aborda. Para C4, C5 y C6 es indispensable. ¿Va en el núcleo? | Servicio del núcleo conectado a un proveedor autorizado, activable por negocio. Validar con un contador. |
| NUC-Q-08 | ¿Qué obligaciones implica custodiar datos de terceros de muchas empresas (Ley 29733) y datos de salud? | Consulta legal antes de vender el primer cliente externo. |
| NUC-Q-14 | ¿Qué datos pueden enviarse a un proveedor de IA y con qué consentimiento? | Por defecto, solo la descripción del negocio y nunca datos de sus clientes. |

## Núcleo

| ID | Pregunta | Propuesta del análisis |
|----|----------|------------------------|
| NUC-Q-15 | ¿Se necesita contabilidad formal o basta con un P&L de gestión? | P&L de gestión; no reemplaza al sistema contable. |
| NUC-Q-16 | ¿Multimoneda en el núcleo? C2 (viajes) e Inversiones la necesitan. | Sí, por negocio y con tipo de cambio registrado en cada operación. **Confirmado por el piloto (P14, 11/Nov/2026):** tiene inversiones en soles y en dólares, así que la multimoneda entra en la etapa 2. |
| NUC-Q-26 | En el tablero, ¿qué representa el "monto" de cada negocio: ingresos del mes, acumulado anual o patrimonio? ¿Cómo se define el objetivo? | 🟢 **Respondida por el cliente (10/Nov/2026):** ingresos **cobrados**. Meta de alquileres: ocupación total; meta de otros negocios: crecimiento de clientes ([5.3](05-reglas-de-negocio-y-calculos.md#53-tablero-estado-del-negocio-frente-al-objetivo)). Falta definir qué muestra la tarjeta de **Inversiones**. |
| NUC-Q-27 | "Alertas por teléfono": ¿SMS, llamada automática o WhatsApp? | SMS en la etapa 2 (barato); WhatsApp en la etapa 3 |
| NUC-Q-28 | ¿El plazo de 10 años aplica a todo o solo a lo tributario? ¿Desde qué fecha se cuenta? Validar con un contador (el Código Tributario fija plazos de conservación y prescripción). | Conservar 10 años todo lo que tenga monto o comprobante |
| NUC-Q-29 | ¿Un analista puede asignar tareas a otro analista o solo el dueño asigna? | Ambos pueden; el cierre lo aprueba quien asignó |
| NUC-Q-30 | ¿La calculadora es una calculadora simple o calculadoras de negocio (rendimiento, interés de plazo fijo, incremento de alquiler)? | Empezar con una simple + las de negocio que ya existen como fórmulas |