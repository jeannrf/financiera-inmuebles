# 01. Visión y modelo de negocio

## 1.1 Qué estamos construyendo

Un **SaaS de gestión para empresarios con uno o varios negocios**. El cliente percibe que tiene
"su software" para cada negocio. Por dentro hay **un solo código base**: un núcleo común y piezas
reutilizables que se combinan según el tipo de negocio. A esa capacidad interna la llamamos
**fábrica de software oculta**: el cliente no la ve, el equipo la opera y la va ampliando.

La idea se apoya en una observación: los negocios se parecen más de lo que parece. Un restaurante y una
ferretería venden mucho y controlan stock; una clínica y un gimnasio venden bloques de tiempo y paquetes.
No hace falta escribir cada software desde cero. Por eso agrupamos los negocios en **6 clústeres**
([mapa de clústeres](10-mapa-de-clusters-y-reutilizacion.md)).

## 1.2 Cómo se llegó aquí

El proyecto empezó para un cliente con un negocio inmobiliario y uno financiero. Ese análisis sigue vigente,
pero ahora es **un caso** dentro de la plataforma:

- El negocio inmobiliario es una vertical del [Clúster 1](../../clusters/cluster-1-activos-alquileres-espacios/README.md).
- El negocio financiero no encaja en ninguno de los 6 clústeres, así que es un [módulo complementario](../../modulos/inversiones-y-liquidez/README.md) ([decisión NUC-Q-01](08-preguntas-abiertas.md#decisiones-tomadas)).
- El cliente sigue siendo el piloto: su entrega no cambia, solo cómo se organiza por dentro.

## 1.3 Modelo comercial [EQUIPO]

1. **Primer software:** el cliente contrata la plataforma para su primer negocio, armada sobre el núcleo.
2. **Negocios adicionales:** cuando quiere gestionar otro negocio, lo solicita y **se paga aparte**.
3. **Asistencia:** el armado del negocio nuevo se hace **con IA y soporte humano**. La IA propone; una persona revisa y publica.

El costo de un negocio adicional depende de cuánto ya existe en la fábrica:

| Caso | Qué pide el cliente | Qué hace el equipo | Esfuerzo | ¿Toca el núcleo? |
|------|---------------------|--------------------|----------|------------------|
| **A** | Un negocio de una vertical que ya existe | Activa la plantilla y configura | Horas o días | No |
| **B** | Una vertical nueva en un clúster que ya existe | Crea la plantilla; quizá algo de código en el clúster | Días o semanas | No |
| **C** | Un negocio de un clúster aún no construido | Construye el paquete del clúster y, si falta, un motor | Semanas o meses | No debería; se amplía por puntos de extensión |
| **D** | Algo muy particular de un solo cliente | Se evalúa como desarrollo a medida o se rechaza | Variable | Nunca |

> **Por qué esta tabla importa:** es lo que hace viable el negocio. El caso A da margen alto y el C es una
> inversión que se paga con los siguientes clientes del clúster. Si el caso D se acepta sin control, la plataforma
> se convierte en N proyectos a medida.

## 1.4 Objetivos de la plataforma

| ID | Objetivo |
|----|----------|
| OE-NUC-01 | Poner en marcha un negocio de una vertical existente **sin escribir código** |
| OE-NUC-02 | Añadir un negocio a un cliente **sin afectar** sus otros negocios ni a otros clientes |
| OE-NUC-03 | Mantener **un solo código base** en todo el producto |
| OE-NUC-04 | Dar al dueño una **vista consolidada** de todos sus negocios frente a sus objetivos |
| OE-NUC-05 | Controlar **quién ve qué** con roles configurables por negocio |
| OE-NUC-06 | Ofrecer servicios comunes listos: finanzas, directorio, documentos, alertas, notificaciones y auditoría |
| OE-NUC-07 | Reducir con IA el tiempo de armado de un negocio, siempre con revisión humana |

## 1.5 Qué significa "que el software no se rompa"

Es el requisito central del cambio y debe poder comprobarse:

- Activar un negocio nuevo **no cambia el comportamiento** de los negocios existentes.
- Cada cliente está **aislado**: un error o una carga alta de uno no expone ni bloquea a otro.
- Las verticales se **versionan**: una mejora de plantilla no se aplica a un cliente sin control.
- Los clústeres dependen del núcleo y **nunca al revés**, y un clúster no depende de otro.
- Las pruebas del núcleo y de cada paquete se ejecutan antes de cada publicación.

## 1.6 Riesgos que introduce este cambio

| Riesgo | Por qué importa | Respuesta propuesta |
|--------|-----------------|---------------------|
| **Propiedad intelectual** | El producto será de una empresa propia del equipo ([NUC-Q-09](08-preguntas-abiertas.md#decisiones-tomadas)), pero el cliente piloto aún no lo sabe y la empresa no está constituida. | Comunicarlo antes de hablar de precio y resolver [NUC-Q-17](08-preguntas-abiertas.md) |
| **Capacidad del equipo** | Son 3 personas en tiempo parcial y unos 2 semestres. No alcanza para 6 clústeres. | Construir núcleo + Clúster 1; los demás quedan solo analizados ([fases](07-fases-y-alcance.md)) |
| **Fábrica prematura** | Generalizar con un solo negocio real suele producir abstracciones equivocadas. | Sacar lo genérico del piloto y validarlo con un segundo clúster antes de crear herramientas |
| **Límite de los metadatos** | Campos y estados se configuran, pero un Kardex o un prorrateo son lógica. | Separar metadato y código desde el diseño ([dominio](02-dominio-nucleo.md#23-qué-es-metadato-y-qué-es-código)) |
| **Datos personales** | Pasamos a custodiar datos de terceros de muchos clientes, incluidos datos de salud en el Clúster 4. | Aislamiento por cliente; rol de encargado de tratamiento ante la Ley 29733, a validar con un abogado |
| **Despliegue en servidores y escritorio** | El cliente pidió web para pequeñas, **escritorio** para medianas y grandes y **servidores en vez de la nube** ([CLI-Q-04](../../clientes/cliente-piloto/02-preguntas-abiertas.md)). Instalar por cliente encarece el soporte y las actualizaciones. | Un solo backend instalable; el escritorio empaqueta la misma interfaz web ([arquitectura](../04-arquitectura/README.md#modelo-de-despliegue-pedido-por-el-cliente-cli-q-04-respondida-el-10112026), [NUC-Q-31 a NUC-Q-33](08-preguntas-abiertas.md)) |
| **Pérdida de foco del piloto** | El cliente "va a exigir como en una empresa" y hay reunión prevista el ~28 de noviembre de 2026. | Su alcance y fechas no se mueven por este cambio interno |
