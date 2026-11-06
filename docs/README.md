# Plataforma de Gestión Multinegocio: Documentación

SaaS de gestión para empresarios con uno o varios negocios: **un solo núcleo** y una **fábrica de software oculta** que
arma el software de cada negocio a partir de **6 clústeres** de negocios parecidos.

**Empieza por:** [Visión y modelo de negocio](general/01-analisis-negocio/01-vision-y-modelo-de-negocio.md) → [Mapa de clústeres](general/01-analisis-negocio/10-mapa-de-clusters-y-reutilizacion.md) → el clúster que te interese.

## Estructura

```
docs/
├── general/                  ← Lo común a TODOS los negocios (núcleo y plataforma)
│   ├── 01-analisis-negocio/
│   ├── 02-srs/
│   ├── 03-modelado/
│   ├── 04-arquitectura/
│   ├── 05-ux/
│   └── 06-gestion/           ← Cronograma y propuesta comercial (solo existe aquí)
│
├── clusters/                 ← Lo particular de cada TIPO de negocio
│   └── cluster-N-nombre/
│       ├── 01-analisis-negocio/
│       ├── 02-srs/
│       ├── 03-modelado/
│       ├── 04-arquitectura/  ← Solo lo que agrega al núcleo
│       └── 05-ux/
│
├── modulos/                  ← Complementos que no son un tipo de negocio
│   └── inversiones-y-liquidez/
│
└── clientes/                 ← Lo particular de cada CLIENTE (compromisos, datos, reuniones)
    └── cliente-piloto/
```

## Dónde va cada cosa

| Si es… | Va en… | Ejemplo |
|--------|--------|---------|
| Común a cualquier negocio | `general/` | Roles, tablero, cierre de mes |
| Común a un tipo de negocio | `clusters/cluster-N/` | Prorrateo, Kardex, agenda sin choques |
| Un complemento de cualquier dueño | `modulos/` | Portafolio de inversiones |
| De un cliente específico | `clientes/` | Fecha de reunión, sus edificios, sus cifras |

> **Regla contra la duplicación:** el SRS, el modelado y la arquitectura de un clúster documentan **solo lo que agregan** al núcleo y lo referencian.
> Aunque cada clúster tiene sus documentos, **el software es uno solo**.

## Estado

| Parte | Análisis de negocio | Validación | SRS, modelado, arquitectura, UX |
|-------|---------------------|------------|----------------|
| [General](general/01-analisis-negocio/00-README.md) | ✅ Borrador v0.2 | Modelo SaaS sin validar con el cliente | ⏳ Pendiente |
| [Clúster 1: Activos y Alquileres](clusters/cluster-1-activos-alquileres-espacios/README.md) | ✅ Borrador v0.2 | 🟢 Cliente real (1.1 y 1.2) | ⏳ Pendiente |
| [Clúster 2: Comercial de Alto Valor](clusters/cluster-2-comercial-alto-valor/README.md) | ✅ Borrador v0.1 | 🟡 Hipótesis | ⏳ Pendiente |
| [Clúster 3: Servicios Profesionales](clusters/cluster-3-servicios-profesionales-proyectos/README.md) | ✅ Borrador v0.1 | 🟡 Hipótesis | ⏳ Pendiente |
| [Clúster 4: Citas y Suscripciones](clusters/cluster-4-citas-agendas-suscripciones/README.md) | ✅ Borrador v0.1 | 🟡 Hipótesis | ⏳ Pendiente |
| [Clúster 5: Servicio Técnico](clusters/cluster-5-servicio-tecnico-campo/README.md) | ✅ Borrador v0.1 | 🟡 Hipótesis | ⏳ Pendiente |
| [Clúster 6: Comercio y Distribución](clusters/cluster-6-comercio-distribucion-produccion/README.md) | ✅ Borrador v0.1 | 🟡 Hipótesis | ⏳ Pendiente |
| [Módulo: Inversiones y Liquidez](modulos/inversiones-y-liquidez/README.md) | ✅ Borrador v0.2 | 🟢 Cliente real | ⏳ Pendiente |
| [Cliente piloto](clientes/cliente-piloto/README.md) | ✅ Primera reunión | 🟡 Por confirmar con el cliente | No aplica |

## Convenciones

**Origen de la información**

| Marca | Significado |
|-------|-------------|
| `[CONFIRMADO]` | El cliente piloto lo dijo claramente |
| `[EQUIPO]` | Decisión del equipo, aún sin validar con un cliente |
| `[MAPEO]` | Viene del documento de mapeo de verticales |
| `[INFERIDO]` | Lo deducimos del contexto; hay que validarlo |
| `[PROPUESTO]` | Añadido por el análisis; requiere decisión |
| `[PREGUNTA xxx]` | Depende de una pregunta abierta |

Las cifras de ejemplo son ilustrativas y **no** son datos reales de ningún cliente.

**IDs con prefijo de ámbito**

| Prefijo | Ámbito | Tipos |
|---------|--------|-------|
| `NUC-` | Núcleo y plataforma | `NUC-P-00` proceso · `NUC-RN-01` regla · `NUC-RF-01` y `NUC-RNF-01` requerimientos · `NUC-Q-01` pregunta |
| `C1-` a `C6-` | Clúster | `C1-P-03`, `C6-RN-07`… |
| `INV-` | Módulo de inversiones | `INV-P-12`, `INV-RF-60`… |
| `CLI-` | Cliente piloto | `CLI-Q-03` |

Del análisis original se conservaron los **números** al añadir el prefijo: el antiguo `RF-25` es `C1-RF-25`, por lo que hay saltos de numeración. Las preguntas `P13` pasaron a `C1-Q-13` para no confundirse con los procesos `P-13`.

## Cómo añadir un negocio a la documentación

1. **Clasifícalo** con el [árbol de decisión](general/01-analisis-negocio/10-mapa-de-clusters-y-reutilizacion.md#102-cómo-clasificar-un-negocio-nuevo).
2. **Si la vertical existe:** crea su carpeta en `clientes/` y solo documenta sus diferencias.
3. **Si es una vertical nueva:** añade su sección en cada archivo del análisis del clúster.
4. **Si no encaja en ningún clúster:** no crees una carpeta todavía; abre una pregunta en [general](general/01-analisis-negocio/08-preguntas-abiertas.md).

## Dónde quedó el análisis original

| Archivo anterior (`01-analisis-negocio/`) | Dónde está ahora |
|-------------------------------------------|------------------|
| `00-README` | [cliente-piloto/README](clientes/cliente-piloto/README.md) (resumen) y este archivo |
| `01-contexto-y-objetivos` | [cliente-piloto/01](clientes/cliente-piloto/01-contexto-y-compromisos.md) y [general/01](general/01-analisis-negocio/01-vision-y-modelo-de-negocio.md) |
| `02-dominio-inmobiliario` | [C1/02](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/02-dominio.md) y [cliente-piloto/03](clientes/cliente-piloto/03-configuracion-y-datos.md) |
| `03-dominio-financiero` | [Inversiones/02](modulos/inversiones-y-liquidez/01-analisis-negocio/02-dominio.md) |
| `04-actores-roles-privilegios` | [C1/03](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/03-actores-roles-privilegios.md), [general/03](general/01-analisis-negocio/03-actores-roles-privilegios.md), [Inversiones/03](modulos/inversiones-y-liquidez/01-analisis-negocio/03-actores-roles-privilegios.md) |
| `05-procesos-de-negocio` (reemplazado por la versión nueva) | [general/04](general/01-analisis-negocio/04-procesos-de-negocio.md), [C1/04](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/04-procesos-de-negocio.md), [Inversiones/04](modulos/inversiones-y-liquidez/01-analisis-negocio/04-procesos-de-negocio.md) |
| `06-reglas-de-negocio-y-calculos` | [general/05](general/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md), [C1/05](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md), [Inversiones/05](modulos/inversiones-y-liquidez/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md) |
| `07-requerimientos-preliminares` | [general/06](general/01-analisis-negocio/06-requerimientos-preliminares.md), [C1/06](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/06-requerimientos-preliminares.md), [Inversiones/06](modulos/inversiones-y-liquidez/01-analisis-negocio/06-requerimientos-preliminares.md) |
| `08-fases-y-alcance` | [general/07](general/01-analisis-negocio/07-fases-y-alcance.md), [C1/07](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/07-fases-y-alcance.md), [Inversiones/07](modulos/inversiones-y-liquidez/01-analisis-negocio/07-fases-y-alcance.md) |
| `09-preguntas-abiertas` | [C1/08](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md), [Inversiones/08](modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md), [cliente-piloto/02](clientes/cliente-piloto/02-preguntas-abiertas.md) |
| `10-glosario` | [C1/09](clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/09-glosario.md), [Inversiones/09](modulos/inversiones-y-liquidez/01-analisis-negocio/09-glosario.md) |
