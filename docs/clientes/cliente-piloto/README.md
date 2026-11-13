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
| ~~Tercer negocio~~ | [CLI-Q-08](02-preguntas-abiertas.md) | **Descartado por ahora** (respuesta del 10/Nov/2026): solo inmobiliario e inversiones |

## Índice

| Archivo | Contenido |
|---------|-----------|
| [01-contexto-y-compromisos.md](01-contexto-y-compromisos.md) | Quién es, su problema, objetivos, modo de trabajo y compromisos |
| [02-preguntas-abiertas.md](02-preguntas-abiertas.md) | Temas comerciales y generales a tratar con este cliente |
| [03-configuracion-y-datos.md](03-configuracion-y-datos.md) | Sus zonas, información actual en Excel y cifras de ejemplo |
| [04-cuestionario-validacion-reunion1.md](04-cuestionario-validacion-reunion1.md) | Pliego ejecutivo de 14 preguntas clave, solicitud de insumos (Issue FIN-01) y **respuestas del cliente** (P3–P14) |

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

## Respuestas al cuestionario (10 y 11/Nov/2026)

- **Entrega:** web para empresas pequeñas, app de escritorio para medianas y grandes, en **servidores** en lugar de la nube.
- **Tamaño:** 1 analista y 11 unidades (departamentos, alquiler en mercado y cocheras). Sin tercer negocio por ahora.
- **Tablero:** mide lo **cobrado**; su meta inmobiliaria es tener **todo alquilado**.
- **Cobranza:** alerta al dueño a los **7 días** por correo y bandeja; pagos parciales sí; **sin intereses** por mora.
- **Analista:** ve montos individuales y comprobantes, **nunca** totales (para que no negocie su sueldo con las ganancias).
- **Prorrateo:** proporcional al consumo de cada medidor, por suministro (agua + alcantarillado, luz).
- **Rendimiento inmobiliario (11/Nov):** alquiler por m² frente al precio de compra nuevo por m² de la zona, depreciado 1 % por año; el analista hace el estudio de mercado.
- **Incobrable (11/Nov):** a los 7 días sin pedido de pago por partes, con corte de agua y luz (a validar legalmente).
- **Bolsa (11/Nov):** rendimiento = (venta − compra + utilidades) / compra, llevado a un año con regla de tres.
- **Monedas (11/Nov):** soles y dólares; no quiere ver ganancias estimadas de acciones no vendidas.
- **Procesos (13/Nov):** el analista recibe los pagos de servicios, sube las fotos de limpieza que le mandan los inquilinos (con estado *Incumplido*), ingresa la tasa media de plazo fijo para comparar y **confirma los incobrables**. Un mes cerrado solo se reabre si se cobró la deuda. **No hay dossier de desalojo** en el sistema.

Detalle: Secciones [3](04-cuestionario-validacion-reunion1.md#sección-3-respuestas-del-cliente-10-de-noviembre-de-2026), [4](04-cuestionario-validacion-reunion1.md#sección-4-respuestas-del-cliente-11-de-noviembre-de-2026) y [5](04-cuestionario-validacion-reunion1.md#sección-5-conciliación-de-procesos-del-clúster-1-13-de-noviembre-de-2026) del cuestionario.
