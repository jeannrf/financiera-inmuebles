# Análisis del negocio: Software de Gestión Multinegocio

> **Fuente:** transcripción de la 1.ª reunión con el cliente (octubre 2026).
> **Estado:** borrador v0.1 del análisis, que el equipo tiene que validar con el cliente.
> **Equipo:** 3 estudiantes de Ingeniería de Software.

## Qué es este documento

Es el análisis ordenado de lo que el cliente pidió en la primera reunión. Sirve de base
para el siguiente paso, la **Especificación de Requisitos de Software (SRS)**, y para los
modelos (casos de uso, dominio, base de datos y arquitectura).

Convenciones usadas en todos los archivos:

- **[CONFIRMADO]**: el cliente lo dijo claramente.
- **[INFERIDO]**: lo deducimos del contexto; hay que validarlo.
- **[PREGUNTA Pxx]**: depende de una pregunta abierta (ver `09-preguntas-abiertas.md`).
- Las cifras de ejemplo vienen de la reunión y **no** son datos reales del cliente.

## Índice

| # | Archivo | Contenido |
|---|---------|-----------|
| 01 | [01-contexto-y-objetivos.md](01-contexto-y-objetivos.md) | Quién es el cliente, el problema, los objetivos y los compromisos acordados |
| 02 | [02-dominio-inmobiliario.md](02-dominio-inmobiliario.md) | Negocio de alquiler de departamentos: entidades y conceptos |
| 03 | [03-dominio-financiero.md](03-dominio-financiero.md) | Cuentas, plazos fijos y Bolsa de Valores de Lima |
| 04 | [04-actores-roles-privilegios.md](04-actores-roles-privilegios.md) | Usuarios del sistema y qué puede ver o hacer cada uno |
| 05 | [05-procesos-de-negocio.md](05-procesos-de-negocio.md) | Procesos actuales (AS-IS) y propuestos (TO-BE) |
| 06 | [06-reglas-de-negocio-y-calculos.md](06-reglas-de-negocio-y-calculos.md) | Reglas y fórmulas: rendimiento, UIT, prorrateo, trading, etc. |
| 07 | [07-requerimientos-preliminares.md](07-requerimientos-preliminares.md) | Requerimientos funcionales y no funcionales (borrador) |
| 08 | [08-fases-y-alcance.md](08-fases-y-alcance.md) | Propuesta de entrega en 3 etapas |
| 09 | [09-preguntas-abiertas.md](09-preguntas-abiertas.md) | Dudas para resolver con el cliente |
| 10 | [10-glosario.md](10-glosario.md) | Términos del negocio |

## Resumen en una página

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

## Entregables que pidió el cliente para la próxima reunión (~1 mes, en un coworking)

1. Un **borrador o boceto en PowerPoint** con lo que entendimos: la estructura, la información
   y los bocetos dibujados de la interfaz.
2. Los **requerimientos funcionales y no funcionales** y un **modelo conceptual** del sistema.
3. La **propuesta por etapas** (qué entra en cada una y qué no se hará).
4. Después de validar: un **cronograma** (MS Project o un Gantt equivalente), **quién hace qué**,
   y el **precio**.

## Próximos pasos propuestos (después de este análisis)

```
docs/
├── 01-analisis-negocio/          ← (este conjunto de archivos)
├── 02-srs/
│   └── SRS.md                    ← IEEE 830 / ISO 29148: propósito, alcance, RF con ID,
│                                    RNF, casos de uso, restricciones, criterios de aceptación
├── 03-modelado/
│   ├── casos-de-uso.md           ← diagrama general + especificación por caso de uso
│   ├── modelo-de-dominio.md      ← diagrama de clases conceptual
│   ├── modelo-er.md              ← entidad-relación (SQL)
│   ├── actividades.md            ← cobro mensual, prorrateo, cierre de mes
│   └── estados.md                ← estados de pago, contrato, tarea de limpieza
├── 04-arquitectura/
│   ├── arquitectura.md           ← C4 (contexto, contenedores, componentes) + stack
│   └── decisiones/ADR-001...     ← registro de decisiones (web o escritorio, BD, etc.)
├── 05-ux/
│   └── wireframes/               ← bocetos de pantallas
└── 06-gestion/
    ├── cronograma.md             ← Gantt / MS Project
    └── propuesta-comercial.md    ← alcance por etapa, precio, propiedad intelectual
```
