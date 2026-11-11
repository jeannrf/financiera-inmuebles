# 03. Actores, roles y privilegios

Los actores comunes están en [el documento general](../../../general/01-analisis-negocio/03-actores-roles-privilegios.md).

## 3.0 Actores adicionales por vertical [INFERIDO]

| Vertical | Actor | Descripción |
|----------|-------|-------------|
| 1.1 | **Propietario tercero** | Dueño del inmueble que encarga la administración. Recibe liquidaciones y ve solo lo suyo |
| 1.1 | **Agente inmobiliario** | Comercializa y recibe comisión |
| 1.2 | **Residente / Junta** | Consulta su estado de cuenta; la junta ve la morosidad del edificio |
| 1.3 | **Counter / Patio** | Hace la entrega y la devolución del bien |
| 1.3 | **Mecánico / Taller** | Da mantenimiento y cierra la unidad para el alquiler |
| 1.4 | **Recepción / Community manager** | Atiende miembros, paquetería y reservas de salas |

La matriz siguiente es la de la vertical piloto, con **Dueño** y **Analista**.

## 3.1 Actores

| Actor | Tipo | Descripción |
|-------|------|-------------|
| **Dueño / Gerente** (el cliente) | Usuario principal (administrador) | Ve todo: montos, ganancias, rendimientos y valorización. Aprueba gastos, cierra meses, define objetivos y montos. |
| **Analista** (N analistas) | Usuario operativo | Hace la "parte mecánica": registra pagos, sube vouchers, ingresa lecturas, hace seguimiento de cobros y gestiona el rol de limpieza. **No ve dinero agregado ni ganancias.** |
| **Inquilino** | Actor externo (no usa el sistema en las etapas 1-2) [PREGUNTA C1-Q-30] | Recibe notificaciones (recibos de servicios, recordatorios, cumpleaños). Envía vouchers y fotos por WhatsApp. |
| **Sistema (tiempo / planificador)** | Actor automático | Genera cuotas mensuales, evalúa atrasos y envía alertas y correos programados. |
| **Servicio de correo / SMS** | Sistema externo | Canal de envío de alertas. |
| **Proveedores de servicios** (agua y luz) | Externo, sin interacción con el sistema | Emiten los recibos que se registran manualmente. |
| **Bróker / Bancos** | Externo, sin interacción en las etapas 1-2 | Fuente de los datos que se ingresan a mano. |

> El cliente pidió explícitamente que los analistas puedan ser **N**, y que cada nuevo usuario
> tenga un **cargo** que determina sus privilegios. Es razonable modelar un **RBAC**
> (control de acceso basado en roles) con roles configurables, empezando por *Dueño* y *Analista*.

## 3.2 Matriz preliminar de privilegios

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Analista |
|---------------|:-----:|:--------:|
| Tablero de negocios (montos frente a objetivos) | ✅ | ❌ |
| Ver lista de cobros del día y de la semana | ✅ | ✅ |
| Registrar pago y subir voucher | ✅ | ✅ |
| Verificar o validar voucher | ✅ | ✅ [CONFIRMADO — P9] |
| Ver el **monto individual** de la cuota de un inquilino y su saldo pendiente | ✅ | ✅ [CONFIRMADO — P9] |
| Ver totales recaudados, ganancias y rendimiento % | ✅ | ❌ [CONFIRMADO — P9] |
| Ver **sumas o subtotales** en listas de cobro, exportaciones o reportes ([NUC-RN-30](../../../general/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md)) | ✅ | ❌ [CONFIRMADO — P9] |
| Ver indicador de ocupación del negocio | ✅ | ❌ [INFERIDO] |
| Ver valor del inmueble, UIT y mejoras | ✅ | ❌ |
| Registrar inquilinos, documentos (DNI, boleta) | ✅ | ✅ |
| Crear o editar departamentos e inmuebles | ✅ | ❌ [INFERIDO] |
| Definir monto de alquiler e incrementos programados | ✅ | ❌ [INFERIDO] |
| Ingresar lecturas de medidores y recibos de servicios | ✅ | ✅ |
| Enviar recibos de servicios a inquilinos | ✅ | ✅ |
| Gestionar el rol de limpieza (marcar cumplido o incumplido) | ✅ | ✅ |
| Solicitar gasto de mantenimiento | ✅ | ✅ |
| **Aprobar** gasto de mantenimiento o mejora | ✅ | ❌ |
| Registrar mejoras al inmueble | ✅ | ❌ [INFERIDO] |
| Cerrar mes (candado) | ✅ | ❌ |
| Calificación (semáforo) de inquilinos | ✅ | 👁 [INFERIDO] |
| Gestionar usuarios y roles | ✅ | ❌ |
| Enviar mensajes internos al dueño | ✅ | ✅ |

## 3.3 Alertas por rol

| Alerta | Destinatario | Canal |
|--------|--------------|-------|
| Lista de pagos que vencen **esta semana** | Analista | Sistema + correo |
| Hoy le toca pagar a X | Analista | Sistema |
| Pago con atraso ≥ N₁ días (nivel 1) [PREGUNTA C1-Q-56: valor de N₁] | **Analista** | Sistema + correo |
| Pago aún sin regularizar ≥ **7 días** (nivel 2, N₂ configurable) [CONFIRMADO — P7] | **Dueño / Gerente** | **Correo electrónico + bandeja del sistema** [CONFIRMADO — P7] |
| Renovación de contrato próxima | Dueño (y analista [INFERIDO]) | Sistema + correo |
| Gasto pendiente de aprobación | Dueño | Mensaje interno |
| Negocio por debajo del objetivo (en rojo) | Dueño | Tablero |
| Cumpleaños del inquilino | Inquilino (saludo automático) | Correo [PREGUNTA C1-Q-14] |

> **Por qué la alerta escala:** en la reunión el cliente dijo que la alerta iba directa al dueño, para enterarse de la
> deuda y a la vez **controlar al analista** ("mata dos pájaros de un tiro"). En la PPT pide "al analista y luego al
> gerente". Se adopta el escalamiento ([C1-RN-38](05-reglas-de-negocio-y-calculos.md), pendiente de confirmar en
> [C1-Q-56](08-preguntas-abiertas.md)), y el nivel 2 llega al dueño **aunque el analista no haga nada**, con lo que se
> conserva el control sobre el analista.

> **Por qué el analista no ve totales** [CONFIRMADO — P9]: necesita el monto individual y el comprobante para cobrar y verificar,
> pero si ve la recaudación total puede deducir las ganancias del negocio y **pedir un aumento** basándose solo en ellas.
> Por eso la lista semanal de cobros del analista muestra montos por inquilino **sin fila de total**, y el control se aplica en el servidor.
