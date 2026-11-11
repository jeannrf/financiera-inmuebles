# 01. Contexto y compromisos del cliente piloto

## 1.1 El cliente

- Es el padre de un compañero del equipo. Fue gerente en Claro, así que conoce la gestión de
  proyectos en empresas y **va a exigir como en una empresa**: fechas, cronograma y entregables.
- Tiene **dos negocios activos**. Mencionó abrir **un tercero** (presupuestos de construcción), pero el
  10/Nov/2026 confirmó que **por ahora solo** se enfoca en el inmobiliario y las inversiones ([CLI-Q-08](02-preguntas-abiertas.md)).
- Hoy gestiona todo con **Excel**, **WhatsApp** (un grupo general con los inquilinos) y revisión manual.

## 1.2 El problema

> "Lo que necesito yo es **tiempo**." "No estar ahí como un idiota."

- Pierde tiempo en tareas mecánicas: revisar quién pagó, comparar vouchers, calcular la luz y el
  agua de cada departamento, perseguir a los morosos y calcular cuánto rinde cada inversión.
- Tiene riesgos que hoy no controla:
  - **Vouchers duplicados o equivocados.** Un inquilino manda el voucher de otro mes o de otro
    departamento ("el del cuarto piso te manda el del segundo").
  - **Un analista que no avisa** de los atrasos ("si no te ha dicho que el 401 no ha pagado, te está
    chambeando").
  - **Deudas de servicios** que deja un inquilino que se va.
  - No sabe con precisión si un inmueble **rinde más o menos que un plazo fijo**.

## 1.3 Objetivo general

Construir un **software de gestión multinegocio** que **automatice** los procesos operativos y
de control de los negocios inmobiliario y financiero. Así el dueño libera tiempo para abrir
nuevos negocios, y el sistema puede **crecer a N negocios** y **adaptarse a otros rubros**.

## 1.4 Objetivos específicos

| ID | Objetivo |
|----|----------|
| OE-01 | Controlar el cobro de alquileres y servicios con **alertas automáticas** de vencimiento y morosidad |
| OE-02 | **Archivar** vouchers, recibos y documentos por inquilino y por período, y consultarlos fácilmente |
| OE-03 | Calcular el **prorrateo** de agua y luz por consumo y generar el resumen para cada inquilino |
| OE-04 | Mantener el **valor actualizado** de cada inmueble (UIT + mejoras) y su **rendimiento** mensual y anual |
| OE-05 | Registrar el **historial** de cada inquilino y calificarlo (verde, amarillo o rojo) |
| OE-06 | Consolidar las **inversiones financieras** con su rendimiento %, y generar el reporte de ganancias para el impuesto a la renta |
| OE-07 | Mostrar un **tablero** con todos los negocios y su avance frente a los objetivos |
| OE-08 | Controlar **quién ve qué** mediante roles (dueño y analistas) |
| OE-09 | Permitir **cerrar** cada mes (candado) cuando todo está conciliado |

## 1.5 Visión de producto (a largo plazo)

- **Escalable:** hoy tiene **11 unidades** (departamentos, alquiler en mercado y cocheras) y 1 analista; mañana tendrá más edificios y más negocios.
- **"Cuasi universal":** el cliente quiere que, "con cinco cambios", el software se pueda
  adaptar y **vender** a otros rubros (un albañil o constructor con presupuestos automáticos, un
  restaurante con insumos, una empresa con cuentas por cobrar).
  → Para la arquitectura, esto implica un **núcleo genérico** (negocios, usuarios, roles, cobros,
  documentos, alertas, tablero) y **módulos por rubro**.
- **Deseos para el futuro (etapa 3 o después):** recibir WhatsApp dentro del software, un
  chat o videollamada con el analista, leer vouchers automáticamente y presupuestos de remodelación
  por m².

> **Actualización:** esta visión del cliente es el origen del giro a SaaS. Su "cuasi universal" y sus ejemplos
> (constructor, restaurante, cuentas por cobrar) ahora son la [visión de la plataforma](../../general/01-analisis-negocio/01-vision-y-modelo-de-negocio.md).
> El cliente todavía **no conoce** el modelo SaaS ni sus consecuencias ([CLI-Q-03](02-preguntas-abiertas.md)).

## 1.6 Modo de trabajo acordado

- El cliente da el alcance "ideal". **El equipo dice qué se puede, qué no y en qué etapa.** Lo que
  no se pueda ahora "lo vemos después".
- Entregas **incrementales y funcionales**: cada entrega es una funcionalidad completa que funciona.
  Primero se prueba con datos aleatorios, luego con datos reales del cliente, y él da su
  retroalimentación.
- Plazo indicado por el equipo: **unos dos semestres**, en **tres etapas**.
- La distribución del trabajo debe ser visible: quién hace qué y para cuándo.
- Hay que **hablar siempre con fechas**.

## 1.7 Temas comerciales pendientes (no técnicos, pero hay que decidirlos)

- **Propiedad intelectual: el equipo eligió la opción (A)** (2026-11-06). Falta comunicárselo al cliente. Las opciones planteadas en la reunión fueron:
  - **(A)** El equipo forma una empresa, es dueño del producto y el cliente es su **primer cliente**.
  - **(B)** El cliente es **dueño** del producto y el equipo se compromete a darle mantenimiento y a
    no venderlo.
  - El cliente dijo que "igual van a ganar" con cualquiera de las dos. Hay que tratarlo **antes del
    precio**.
- **Precio y forma de pago por etapa.** Se definen después de validar el alcance.
- **Formalidad:** la próxima reunión será en un **coworking** (el cliente lo paga), con una presentación.

## 1.8 Compromisos para la próxima reunión

| Compromiso | Fecha |
|------------|-------|
| Presentación (PowerPoint) con lo entendido: estructura, información y bocetos de pantallas | ~1 mes después de la 1.ª reunión (aprox. **28 de noviembre de 2026**) [PREGUNTA CLI-Q-01] |
| Requerimientos funcionales y no funcionales + modelo conceptual | Igual |
| Propuesta de las 3 etapas | Igual |
| Cronograma (MS Project o Gantt) y precio | Después de validar el alcance |

## 1.9 Material recibido del cliente

2026-11-06 — PPT *SOFTWARE DE GESTIÓN* (4 diapositivas) con las características macro de los software general, inmobiliario y de finanzas. Sus puntos se incorporaron con la marca `[CONFIRMADO — PPT cliente]`.

## Entregables que pidió el cliente para la próxima reunión (~1 mes, en un coworking)

1. Un **borrador o boceto en PowerPoint** con lo que entendimos: la estructura, la información
   y los bocetos dibujados de la interfaz.
2. Los **requerimientos funcionales y no funcionales** y un **modelo conceptual** del sistema.
3. La **propuesta por etapas** (qué entra en cada una y qué no se hará).
4. Después de validar: un **cronograma** (MS Project o un Gantt equivalente), **quién hace qué**,
   y el **precio**.
