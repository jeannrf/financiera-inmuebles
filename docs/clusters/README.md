# Clústeres

Cada clúster agrupa tipos de negocio que operan y ganan dinero de forma parecida. La comparación completa y el árbol para clasificar
un negocio están en el [mapa de clústeres](../general/01-analisis-negocio/10-mapa-de-clusters-y-reutilizacion.md).

| # | Clúster | Vende | Verticales | Validación |
|---|---------|-------|:----------:|------------|
| 1 | [Activos, Alquileres y Espacios](cluster-1-activos-alquileres-espacios/README.md) | Uso temporal de un bien | 4 | 🟢 Cliente real |
| 2 | [Comercial de Alto Valor](cluster-2-comercial-alto-valor/README.md) | Cierres consultivos | 4 | 🟡 Hipótesis |
| 3 | [Servicios Profesionales por Proyectos](cluster-3-servicios-profesionales-proyectos/README.md) | Conocimiento y entregables | 4 | 🟡 Hipótesis |
| 4 | [Citas, Agendas y Suscripciones](cluster-4-citas-agendas-suscripciones/README.md) | Bloques de tiempo | 4 | 🟡 Hipótesis |
| 5 | [Servicio Técnico en Campo](cluster-5-servicio-tecnico-campo/README.md) | Reparación y mantenimiento | 3 | 🟡 Hipótesis |
| 6 | [Comercio, Distribución y Producción](cluster-6-comercio-distribucion-produccion/README.md) | Bienes físicos | 3 | 🟡 Hipótesis |

## Qué contiene cada clúster

| Carpeta | Contenido |
|---------|-----------|
| `01-analisis-negocio/` | Contexto, dominio, actores, procesos, reglas, requerimientos, fases, preguntas y glosario |
| `02-srs/` | Especificación del clúster; referencia al SRS general |
| `03-modelado/` | Casos de uso, dominio, ER, actividades y estados propios |
| `04-arquitectura/` | Paquete del clúster, motores que activa y decisiones propias |
| `05-ux/` | Pantallas propias |

> Los análisis de 2 a 6 parten del documento de mapeo y son **hipótesis de trabajo**. Antes de pasar al SRS deben validarse con un cliente real del rubro.
