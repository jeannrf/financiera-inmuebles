# 07. Fases y alcance de la plataforma

> **Recomendación del análisis, pendiente de decisión del equipo.** La propuesta conserva las 3 etapas previstas para el
> cliente piloto y añade lo necesario para no cerrar el camino al SaaS.

## 7.1 Principio de corte

Con 3 personas en tiempo parcial y unos 2 semestres, **no se puede construir la plataforma completa**.
Lo que sí es posible y barato ahora es **no bloquearla**. Hay decisiones muy caras de cambiar después:

| Se hace desde el primer día | Se pospone hasta que haya un segundo clúster real |
|-----------------------------|---------------------------------------------------|
| Separar por organización y negocio en todas las tablas | Panel visual para crear plantillas |
| Núcleo y paquetes separados en el código | Asistente IA |
| Vocabulario genérico en el núcleo (Obligación, Contacto) | Publicación por tandas |
| Permisos por rol y por campo | Autoservicio y facturación del SaaS |
| Registro de paquetes, aunque solo exista uno | Motores que el Clúster 1 no use (inventario, agenda) |

> **La fábrica nace como archivos de configuración que el equipo edita.** El panel visual se justifica cuando editar
> esos archivos sea el cuello de botella, no antes.

## 7.2 Hoja de ruta

| Etapa | Objetivo | Núcleo y fábrica | Negocio | Duración estimada |
|-------|----------|------------------|---------|-------------------|
| **1** | El cliente deja el Excel de alquileres | Organización, negocios, roles, documentos, alertas, directorio y CxC básica | [C1: cobranza](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/07-fases-y-alcance.md) | ~4 meses |
| **2** | El dueño ve cuánto gana y cuánto vale cada negocio | Tablero, mensajería, cierre, P&L, plantillas por archivos | C1 completo + [Inversiones](../../modulos/inversiones-y-liquidez/01-analisis-negocio/07-fases-y-alcance.md) | ~4–5 meses |
| **3** | Integraciones y prueba de la fábrica | WhatsApp, OCR, panel interno y exportación | Segundo clúster como prueba real | Después de los 2 semestres, o según avance |
| **4+** | Producto vendible | Asistente IA, autoservicio, facturación del SaaS | Más verticales según la demanda | Por definir |

## 7.3 ¿Qué clúster va después del piloto?

Se decide con clientes reales. Con la información actual, **el mejor candidato es el Clúster 3, vertical 3.3**
(constructoras y presupuestos por partidas), porque:

- ~~El cliente piloto ya mencionó **presupuestos de construcción** como posible tercer negocio.~~ **Actualización 10/Nov/2026:** el piloto confirmó que, por ahora, **no** abrirá un tercer negocio ([CLI-Q-08](../../clientes/cliente-piloto/02-preguntas-abiertas.md)). C3 pierde su cliente real para validar; sigue siendo candidato por reutilización, pero la elección queda abierta hasta que llegue un cliente de otro clúster.
- Según la [matriz](10-mapa-de-clusters-y-reutilizacion.md#103-matriz-de-reutilización), C3 tiene reutilización alta de contratos y cobro recurrente, que ya estará construido.
- Es una prueba exigente: obliga a añadir el motor de tareas e hitos sin tocar el núcleo.

El Clúster 6 es muy atractivo como mercado (muchas ventas), pero es el que menos reutiliza del piloto:
requiere inventario y punto de venta, y su volumen pone a prueba la arquitectura. Conviene llegar a él con la fábrica ya probada.

## 7.4 Fuera de alcance

- Conexión directa con bancos o brókers y cotizaciones de bolsa en tiempo real.
- Declaración tributaria automática ante SUNAT (el sistema solo **calcula y reporta**). La emisión de comprobantes electrónicos se trata aparte en [NUC-Q-07](08-preguntas-abiertas.md).
- Que el sistema "decida" solo si un comprobante es válido.
- Construir los clústeres 2 a 6 dentro de los 2 semestres del piloto: en este período solo se **analizan**.

## 7.5 Reparto sugerido del trabajo

| Persona | Responsabilidad principal | Etapa 1 | Etapa 2 |
|---------|---------------------------|---------|---------|
| Integrante 1 | Núcleo y seguridad | Usuarios, roles, documentos, alertas y correo | Tablero, mensajería, cierre de mes |
| Integrante 2 | Inmobiliario | Inmuebles, inquilinos, contratos, cuotas, pagos | Servicios, prorrateo, limpieza, mantenimiento |
| Integrante 3 | Cálculos y finanzas | Historial, incrementos, reportes e importación de Excel | UIT, rendimiento, calificación, módulo financiero |

La recomendación técnica preliminar se movió a [04-arquitectura](../04-arquitectura/README.md).
