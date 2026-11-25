# Cuestionario de cierre — Ronda 2

**Fecha:** 24 de noviembre de 2026
**Dirigido a:** Cliente Piloto
**Elaborado por:** Equipo de Ingeniería del Proyecto (John, Jeanpier, Ilia)
**Objetivo:** Cerrar las preguntas bloqueantes que dejaron las respuestas del 10 al 13 de noviembre y la PPT del cliente,
confirmar la reunión del ~28 de noviembre y registrar los insumos recibidos, para destrabar el SRS v1.0 (FIN-04, FIN-05,
FIN-06) y el modelo de datos (FIN-07, FIN-08).

> **Cómo funciona esta ronda:** cada punto trae una **propuesta por defecto**. Si el cliente no la objeta, queda **aprobada
> para el SRS** y se marca como `⚙ Default aplicado para SRS` en los archivos de preguntas.

---

## Sección 1: Mensaje para enviar al cliente (WhatsApp o correo)

> *Texto listo para copiar y enviar:*

Estimado [Nombre del Cliente]:

Muchas gracias por sus respuestas y por los Excel de alquileres y servicios; ya los revisamos y nos sirven mucho para el diseño.

Para cerrar el documento de requerimientos antes de la reunión, le pedimos confirmar estos puntos. En cada uno ponemos lo que
haremos **si usted no indica otra cosa**, así que basta con responder solo donde quiera cambiar algo:

1. **Reunión:** sábado **28 de noviembre a las 10:00 a. m.** en el coworking que usted indique (45 min de presentación + 30 min de preguntas). ¿Nos confirma el lugar?
2. **Cliente Fundador:** el sistema será de una empresa del equipo y usted será nuestro **primer cliente**, con precio preferencial y prioridad de soporte. ¿Está de acuerdo?
3. **WhatsApp y videollamada:** los dejamos para la **etapa 3** por el costo de la API oficial de WhatsApp; mientras tanto, mensajes y avisos dentro del sistema y por correo.
4. **Cantidad de departamentos:** el Excel de servicios tiene **9 departamentos** (1A a 4B y 5.º piso), pero usted nos indicó **8**. ¿Cuál es el número correcto? Y el **puesto del mercado**, ¿paga solo el alquiler?
5. **Gas:** en el Excel cada departamento con gas tiene **su propio suministro**. Le cobraremos a cada uno **su recibo de gas tal cual**, sin repartirlo entre todos.
6. **Recibos de agua y luz:** usted paga al proveedor y el analista registra en el sistema el comprobante de ese pago.
7. **Póliza de la bolsa (BVL):** ¿nos puede enviar una póliza de compra o venta (puede tapar los montos)? Sin ella, las comisiones quedarán como datos que usted ingresa en cada operación.

Los demás detalles (punto 8 en adelante del pliego) los aplicaremos como se indica salvo que nos diga lo contrario.

Muchas gracias. Saludos cordiales,
John, Jeanpier e Ilia

---

## Sección 2: Pliego de definiciones con propuesta por defecto

### Bloque A: Reunión y modelo de trabajo

| # | ID | Pregunta | ⚙ Propuesta por defecto |
|---|----|----------|-------------------------|
| 1 | [CLI-Q-01](02-preguntas-abiertas.md) | ¿Fecha, hora y lugar de la reunión? | Sábado **28/11/2026, 10:00 a. m.**, en el coworking que indique el cliente; 45 min de presentación + 30 min de acuerdos |
| 2 | [CLI-Q-03 / CLI-Q-09](02-preguntas-abiertas.md) | ¿Conformidad con la **Opción A** (empresa del equipo y él como Cliente Fundador)? | Acepta: tarifa preferencial, descuento en el mantenimiento y prioridad de soporte |
| 3 | [CLI-Q-10](02-preguntas-abiertas.md) | ¿WhatsApp y videollamada en la etapa 3? | Sí; en las etapas 1 y 2 se usan la bandeja del sistema, los mensajes internos y el correo |

### Bloque B: Bloqueantes que necesitan respuesta

| # | ID | Pregunta | ⚙ Propuesta por defecto |
|---|----|----------|-------------------------|
| 4 | [C1-Q-73](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | ¿8 o 9 departamentos? ¿El puesto de mercado paga servicios o mantenimiento? | Se cargan las unidades del Excel; el puesto paga **solo alquiler** |
| 5 | [INV-Q-27](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md) | Póliza BVL de muestra y comisión del bróker | Comisiones como **parámetros editables por operación** (SAB, BVL, CAVALI, SMV, IGV) |

### Bloque C: Detalles con default (se aplican si no objeta)

| # | ID | Tema | ⚙ Propuesta por defecto |
|---|----|------|-------------------------|
| 6 | [C1-Q-34](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Gas | Cada departamento con gas paga **su propio recibo**, sin prorrateo |
| 7 | [C1-Q-70](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Pago del recibo al proveedor | Lo paga el **dueño**; el **analista** registra el comprobante |
| 8 | [C1-Q-71](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Quién reabre un mes cerrado | Solo el **dueño**, y solo si se cobró una deuda incobrable |
| 9 | [C1-Q-59](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Meta mensual de cobranza del tablero | Suma de los alquileres con **todas las unidades ocupadas** |
| 10 | [C1-Q-60](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Alerta con pago parcial | Los 7 días se cuentan desde el **vencimiento original** |
| 11 | [C1-Q-28](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Día de pago ("30 de cada mes") | Día de pago **por contrato**; si el mes no tiene ese día (febrero), vence el **último día del mes** |
| 12 | [C1-Q-62](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Años de recuperación | Se muestran como **dato secundario** junto al rendimiento por m² |
| 13 | [C1-Q-64](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Tope de depreciación | Máximo **50 %** (configurable) |
| 14 | [C1-Q-65](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Mejoras | No cambian el rendimiento por m²; se suman a la inversión para los años de recuperación |
| 15 | [C1-Q-69](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | Reposición de servicios | Se reponen cuando se cobra la deuda; sin costo de reconexión en el sistema |
| 16 | [NUC-Q-27](../../general/01-analisis-negocio/08-preguntas-abiertas.md) | "Alertas por teléfono" (PPT) | **Correo y bandeja del sistema** en las etapas 1 y 2 (lo que pidió en P7); SMS o WhatsApp en la etapa 3 |
| 17 | [NUC-Q-28](../../general/01-analisis-negocio/08-preguntas-abiertas.md) | Plazo de 10 años (PPT) | Se conserva **10 años** todo lo que tenga monto o comprobante |
| 18 | [INV-Q-39](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md) | EBITDA trimestral (PPT) | Es el de las **empresas donde invierte**; se registra a mano en el módulo de inversiones |
| 19 | [INV-Q-40 / INV-Q-44](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md) | Alerta de ±5 % del precio (PPT) | Se mantiene, con el **precio de cierre ingresado a mano**; no muestra ganancia estimada |
| 20 | [INV-Q-42](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md) | Rendimiento bursátil | Compra y venta **con comisiones**; días calendario, base 365 |

---

## Sección 3: Respuestas ya recibidas (24 de noviembre de 2026)

Respuestas del cliente que cierran parte de la lista del issue sin necesidad de enviarlas:

| ID | Respuesta | Dónde se aplicó |
|----|-----------|-----------------|
| [NUC-Q-31](../../general/01-analisis-negocio/08-preguntas-abiertas.md) | ⏸ Postergada: "por ahora no toca". Solo se da por cierto que habrá **versión web y versión de escritorio** | [Arquitectura](../../general/04-arquitectura/README.md), NUC-RNF-07 |
| [NUC-Q-32](../../general/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 Servidores **operados por el equipo** para los clientes | Arquitectura, NUC-RNF-23 |
| [NUC-Q-33](../../general/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 El piloto prefiere la **web** (tiene pocos negocios); escritorio para empresas más grandes | [Configuración 3.4](03-configuracion-y-datos.md#34-dimensionamiento-actual) |
| NUC-Q-05, NUC-Q-17 | ⏸ Postergadas: no importan por ahora | [Preguntas del núcleo](../../general/01-analisis-negocio/08-preguntas-abiertas.md) |
| [C1-Q-56](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 La alerta al **analista** también es a los **7 días** | C1-RN-38, C1-RF-57, alertas por rol |
| [C1-Q-58](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 **Puesto dentro de un mercado**; **8 departamentos, 2 cocheras, 1 puesto**. Las cocheras tienen contrato, pero no limpieza ni mantenimiento | Dominio C1 (tipos de unidad), C1-RF-60 |
| [C1-Q-62](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 La **UIT no se usa** | C1-RN-09 y C1-RF-45 descartados, B2 descartada, C1-P-08 |
| [C1-Q-63](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 Rendimiento **neto**: se restan impuestos y mantenimiento | B1-bis, C1-RN-43, C1-RF-46 |
| [C1-Q-67](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 Se **cortan los servicios** sin más trámite (el riesgo legal queda registrado por el equipo) | C1-RN-46 |
| [C1-Q-68](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 El sistema **propone al dueño** y **él decide** si es incobrable (reemplaza la respuesta del 13/Nov, en la que confirmaba el analista) | C1-RN-47, C1-P-03, C1-P-10, C1-RF-53, matriz de privilegios |
| [C1-Q-61](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md) | 🟢 Por el Excel: agua y alcantarillado se reparten por separado con el % de consumo de agua | [Configuración 3.2.2](03-configuracion-y-datos.md#322-tabla-de-agua-agua_luzjpg-parte-superior) |
| Excel de alquileres | Hoy se pinta de rojo **toda la fila** del moroso; hay que ajustarlo para marcar solo la cuota vencida | C1-RF-70, [Configuración 3.2.1](03-configuracion-y-datos.md#321-tabla-de-inquilinos-y-alquiler-ejemplojpg) |

---

## Sección 4: Insumos recibidos

| Insumo | Estado | Dónde se documentó |
|--------|--------|--------------------|
| Excel de alquileres (`ejemplo.jpg`) | ✅ Recibido (captura) | [03-configuración, 3.2.1](03-configuracion-y-datos.md#321-tabla-de-inquilinos-y-alquiler-ejemplojpg) |
| Excel de agua y luz (`agua_luz.jpg`) | ✅ Recibido (captura) | [03-configuración, 3.2.2 y 3.2.3](03-configuracion-y-datos.md#322-tabla-de-agua-agua_luzjpg-parte-superior) |
| Voucher de pago típico (Yape, Plin o transferencia) | ⏳ Pendiente | — |
| Recibo real del proveedor (Sedapal, Enel o Luz del Sur) | ⏳ Pendiente | — |
| Póliza de compra o venta BVL | ⏳ Pendiente (punto 7 del mensaje) | [03-configuración, 3.2.4](03-configuracion-y-datos.md#324-póliza-de-la-bvl) |

> Los datos personales de los Excel (nombres, DNI, teléfonos) **no se copian** al repositorio; solo su estructura.
