# 04-arquitectura (general)

_Pendiente: C4 del núcleo, los puntos de extensión y las decisiones técnicas (ADR)._

Las reglas de capas están en [02-dominio-nucleo.md](../01-analisis-negocio/02-dominio-nucleo.md). La arquitectura de cada clúster documenta
**solo lo que agrega** a este núcleo.

## Recomendación técnica preliminar (para discutir en la arquitectura)

- **Aplicación web** (responsiva) en lugar de una app de escritorio: el cliente y los analistas acceden
  desde cualquier laptop o celular, hay una sola instalación, y aprovecha la experiencia del equipo en
  desarrollo web. [PREGUNTA CLI-Q-04]
- **Base de datos relacional (SQL)**, por ejemplo PostgreSQL o MySQL, ya que el dominio es muy relacional.
- **Tareas programadas** (cron o scheduler) para las cuotas y alertas, y un servicio de correo transaccional.
- **Almacenamiento de archivos** fuera de la base de datos (disco o almacenamiento de objetos), con acceso protegido.
- **Monolito modular**: un núcleo (negocios, usuarios, roles, documentos, alertas) y módulos (inmobiliario,
  financiero), lo que deja preparado el crecimiento a N negocios sin complicar el despliegue.

## Decisiones que agrega el modelo SaaS (para discutir) [INFERIDO]

- **Aplicación web:** queda decidida por el modelo SaaS; ya no depende de [CLI-Q-04](../../clientes/cliente-piloto/02-preguntas-abiertas.md), que pasa a ser informativa para el cliente.
- **Multi-tenancy:** una sola base de datos con `organizacion_id` y seguridad a nivel de fila, hasta que algún cliente exija otra cosa.
- **Monolito modular:** núcleo, motores y paquetes como módulos del mismo código, con dependencias comprobadas automáticamente.
- **Metadatos:** archivos versionados en el repositorio para las plantillas; columnas JSON validadas para campos adicionales.
