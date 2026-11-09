# Cliente piloto

> **Fuente:** transcripción de la 1.ª reunión (octubre 2026).
> **Importante:** esta carpeta guarda lo que es **de este cliente**, y no de un tipo de negocio. Cuando lleguen otros
> clientes, cada uno tendrá su carpeta `clientes/<nombre>/` con esta misma forma.

## Qué tiene y dónde se documenta

| Negocio del cliente | Se analiza en | Vertical o módulo |
|---------------------|---------------|-------------------|
| Inmobiliario: construye y alquila departamentos | [Clúster 1](../../clusters/cluster-1-activos-alquileres-espacios/README.md) | 1.1 Inmobiliaria + 1.2 Edificios, como propietario directo |
| Financiero: cuentas, plazos fijos y BVL | [Módulo de inversiones](../../modulos/inversiones-y-liquidez/README.md) | Módulo complementario |
| Transversal: tablero, roles y mensajes | [General](../../general/01-analisis-negocio/00-README.md) | Núcleo |
| Tercer negocio, aún sin definir | [CLI-Q-08](02-preguntas-abiertas.md) | Posiblemente 3.3 Construcción [INFERIDO] |

## Índice

| Archivo | Contenido |
|---------|-----------|
| [01-contexto-y-compromisos.md](01-contexto-y-compromisos.md) | Quién es, su problema, objetivos, modo de trabajo y compromisos |
| [02-preguntas-abiertas.md](02-preguntas-abiertas.md) | Temas comerciales y generales a tratar con este cliente |
| [03-configuracion-y-datos.md](03-configuracion-y-datos.md) | Sus zonas, información actual en Excel y cifras de ejemplo |
| [04-cuestionario-validacion-reunion1.md](04-cuestionario-validacion-reunion1.md) | Pliego ejecutivo de 14 preguntas clave y solicitud de insumos (Issue FIN-01) |

Las preguntas sobre el negocio van en [C1](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) e
[Inversiones](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md). Antes de enviárselas hay que unificarlas en un solo documento.

## Resumen de la 1.ª reunión


El cliente tiene **dos negocios** y quiere abrir un **tercero**. Quiere un software que
**automatice** el trabajo operativo para **ganar tiempo**.

1. **Inmobiliario:** construye edificios y **alquila** los departamentos (no los vende).
   Hoy lleva todo en Excel y WhatsApp. Necesita: control de cobros con **alertas de
   morosidad**, archivo de **vouchers**, **historial** de montos, **incrementos programados**,
   **prorrateo de agua y luz**, **rol de limpieza**, **valorización del inmueble ligada a la UIT**
   más mejoras, **rendimiento mensual y anual**, **calificación de inquilinos**, **cierre de mes** y
   datos para un eventual **juicio de desalojo**.
2. **Financiero:** dinero en **cuentas bancarias**, **depósitos a plazo fijo** y **acciones en la
   BVL**. Necesita ver el monto y el **rendimiento %** de cada instrumento para decidir dónde
   mover el dinero, y un **reporte de ganancias de trading** para el impuesto a la renta.
3. **Transversal:** un **tablero de inicio** con una tarjeta por negocio (monto actual frente al
   objetivo, en verde o rojo), **mensajes internos**, **roles** (dueño y N analistas, y el
   analista no ve montos ni ganancias) y un diseño **escalable a N negocios**. A futuro
   quiere poder **adaptarlo y venderlo** a otros rubros.
