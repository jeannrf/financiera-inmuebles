# 04. Actores, roles y privilegios

## 4.1 Actores

| Actor | Tipo | Descripción |
|-------|------|-------------|
| **Dueño / Gerente** (el cliente) | Usuario principal (administrador) | Ve todo: montos, ganancias, rendimientos y valorización. Aprueba gastos, cierra meses, define objetivos y montos. |
| **Analista** (N analistas) | Usuario operativo | Hace la "parte mecánica": registra pagos, sube vouchers, ingresa lecturas, hace seguimiento de cobros y gestiona el rol de limpieza. **No ve dinero agregado ni ganancias.** |
| **Inquilino** | Actor externo (no usa el sistema en las etapas 1-2) [PREGUNTA P30] | Recibe notificaciones (recibos de servicios, recordatorios, cumpleaños). Envía vouchers y fotos por WhatsApp. |
| **Sistema (tiempo / planificador)** | Actor automático | Genera cuotas mensuales, evalúa atrasos y envía alertas y correos programados. |
| **Servicio de correo / SMS** | Sistema externo | Canal de envío de alertas. |
| **Proveedores de servicios** (agua y luz) | Externo, sin interacción con el sistema | Emiten los recibos que se registran manualmente. |
| **Bróker / Bancos** | Externo, sin interacción en las etapas 1-2 | Fuente de los datos que se ingresan a mano. |

> El cliente pidió explícitamente que los analistas puedan ser **N**, y que cada nuevo usuario
> tenga un **cargo** que determina sus privilegios. Es razonable modelar un **RBAC**
> (control de acceso basado en roles) con roles configurables, empezando por *Dueño* y *Analista*.

## 4.2 Matriz preliminar de privilegios

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Analista |
|---------------|:-----:|:--------:|
| Tablero de negocios (montos frente a objetivos) | ✅ | ❌ |
| Ver lista de cobros del día y de la semana | ✅ | ✅ |
| Registrar pago y subir voucher | ✅ | ✅ |
| Verificar o validar voucher | ✅ | ✅ [PREGUNTA P31] |
| Ver el **monto** de alquiler de un inquilino | ✅ | ⚠ [PREGUNTA P32: el analista necesita saber cuánto cobrar] |
| Ver totales recaudados, ganancias y rendimiento % | ✅ | ❌ |
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
| Módulo financiero (cuentas, plazos, bolsa) | ✅ | ❌ |
| Calificación (semáforo) de inquilinos | ✅ | 👁 [INFERIDO] |
| Gestionar usuarios y roles | ✅ | ❌ |
| Enviar mensajes internos al dueño | ✅ | ✅ |

## 4.3 Alertas por rol

| Alerta | Destinatario | Canal |
|--------|--------------|-------|
| Lista de pagos que vencen **esta semana** | Analista | Sistema + correo |
| Hoy le toca pagar a X | Analista | Sistema |
| Pago con **atraso ≥ N días** (el cliente dijo 5 y también 7) [PREGUNTA P13] | **Dueño** | Correo y/o **SMS** |
| Renovación de contrato próxima | Dueño (y analista [INFERIDO]) | Sistema + correo |
| Gasto pendiente de aprobación | Dueño | Mensaje interno |
| Vencimiento de plazo fijo | Dueño | Sistema + correo [INFERIDO] |
| Negocio por debajo del objetivo (en rojo) | Dueño | Tablero |
| Cumpleaños del inquilino | Inquilino (saludo automático) | Correo [PREGUNTA P14] |

> **Por qué la alerta va directa al dueño:** "Mata dos pájaros de un tiro". El dueño se entera de
> la deuda y además **controla al analista** (si el analista no le avisó, no está haciendo su trabajo).
