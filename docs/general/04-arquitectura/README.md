# 04-arquitectura (general)

_Pendiente: C4 del núcleo, los puntos de extensión y las decisiones técnicas (ADR)._

Las reglas de capas están en [02-dominio-nucleo.md](../01-analisis-negocio/02-dominio-nucleo.md). La arquitectura de cada clúster documenta
**solo lo que agrega** a este núcleo.

## Recomendación técnica preliminar (para discutir en la arquitectura)

- ~~**Aplicación web** (responsiva) en lugar de una app de escritorio~~ → reemplazado por la sección
  [Modelo de despliegue pedido por el cliente](#modelo-de-despliegue-pedido-por-el-cliente-cli-q-04-respondida-el-10112026).
- **Base de datos relacional (SQL)**, por ejemplo PostgreSQL o MySQL, ya que el dominio es muy relacional.
- **Tareas programadas** (cron o scheduler) para las cuotas y alertas, y un servicio de correo transaccional.
- **Almacenamiento de archivos** fuera de la base de datos (disco o almacenamiento de objetos), con acceso protegido.
- **Monolito modular**: un núcleo (negocios, usuarios, roles, documentos, alertas) y módulos (inmobiliario,
  financiero), lo que deja preparado el crecimiento a N negocios sin complicar el despliegue.

## Decisiones que agrega el modelo SaaS (para discutir) [INFERIDO]

- ~~**Aplicación web:** queda decidida por el modelo SaaS~~. Ver la sección siguiente: el cliente pidió también escritorio y servidores.
- **Multi-tenancy:** una sola base de datos con `organizacion_id` y seguridad a nivel de fila, hasta que algún cliente exija otra cosa. *(Con servidores por cliente, la RLS se mantiene igual: protege si luego se agrupan clientes en un mismo servidor.)*
- **Monolito modular:** núcleo, motores y paquetes como módulos del mismo código, con dependencias comprobadas automáticamente.
- **Metadatos:** archivos versionados en el repositorio para las plantillas; columnas JSON validadas para campos adicionales.

## Modelo de despliegue pedido por el cliente (CLI-Q-04, respondida el 10/11/2026)

**Lo que dijo el cliente** [CONFIRMADO]: está de acuerdo con la web, pero quiere
- una **versión web** para **empresas pequeñas**;
- una **aplicación de escritorio** para **empresas medianas y grandes**;
- que se use **servidores en lugar de la nube**.

**Qué cambia:** el análisis suponía un SaaS en la nube con una sola instalación para todos. Ahora el núcleo debe poder
entregarse de más de una forma **sin dejar de ser un solo código base** ([OE-NUC-03](../01-analisis-negocio/01-vision-y-modelo-de-negocio.md#14-objetivos-de-la-plataforma)).

**Propuesta del equipo** [PROPUESTO]:

| Pieza | Empresa pequeña | Empresa mediana o grande |
|-------|-----------------|--------------------------|
| Interfaz | Navegador (web responsiva) | **App de escritorio** que empaqueta la **misma interfaz web** (por ejemplo, Electron o Tauri) |
| Servidor y base de datos | **Servidor dedicado** operado por el equipo, compartido por varias organizaciones pequeñas (aisladas por RLS) | **Servidor propio del cliente** (en su local o centro de datos) o servidor dedicado solo para él |
| Código | El mismo backend y la misma interfaz | El mismo backend y la misma interfaz |
| Actualizaciones | Las publica el equipo | Por versión, con ventana acordada con el cliente |

Así la app de escritorio no es un segundo producto: es una "ventana" instalable sobre la misma aplicación, y "servidores en
vez de la nube" se resuelve con **instalación local o dedicada (on-premise)** del mismo backend.

**Consecuencias para el núcleo:**
- El backend debe poder **instalarse por cliente** (paquete con base de datos, archivos y tareas programadas), no solo en una nube.
- Respaldos, monitoreo y actualizaciones dejan de ser centrales: hay que definir **quién los hace** en un servidor del cliente ([NUC-Q-32](../01-analisis-negocio/08-preguntas-abiertas.md)).
- El correo de alertas necesita salida a internet aunque el servidor esté en el local del cliente.
- Ver [NUC-RNF-07](../01-analisis-negocio/06-requerimientos-preliminares.md) (portabilidad) y [NUC-RNF-23](../01-analisis-negocio/06-requerimientos-preliminares.md) (despliegue).

**Para el cliente piloto** (1 analista, 11 unidades) corresponde la **versión web** [INFERIDO → [NUC-Q-33](../01-analisis-negocio/08-preguntas-abiertas.md)].
La app de escritorio y la instalación en servidor del cliente **no** entran en las etapas 1 y 2 salvo que se decida lo contrario.

Preguntas abiertas: [NUC-Q-31 a NUC-Q-33](../01-analisis-negocio/08-preguntas-abiertas.md).
