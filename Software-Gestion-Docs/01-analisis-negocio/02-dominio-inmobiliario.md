# 02. Dominio inmobiliario (alquiler de departamentos)

## 2.1 Descripción del negocio

El cliente **construye** edificios (es lo más barato; también compra en planos o terminado) y
**alquila** los departamentos. Los ingresos vienen del **alquiler mensual** y además se cobran
(o se trasladan) **servicios**: agua, luz, gas, mantenimiento de áreas comunes y limpieza.

Hay inmuebles en al menos dos zonas, con modalidades distintas:

| Zona | Modalidad de servicios | Ejemplo mencionado |
|------|------------------------|--------------------|
| **San Martín de Porres** (edificio de unos 8 departamentos: 1A, 1B, 2A, 2B, 3B, 5.º piso…) | **El dueño paga** los recibos de agua y luz al proveedor y **cobra a cada inquilino** su parte según su consumo (prorrateo). Los inquilinos tienen un **rol de limpieza**. | Recibo de agua de S/ 300 repartido entre 8 departamentos |
| **Jesús María** (dpto. 501) | El inquilino **paga sus servicios directamente** o paga un paquete con todo incluido (limpieza y mantenimiento), unos **S/ 284–300** | Inquilino médico que prefiere pagar a limpiar |

> Motivo del cliente para pagar él mismo los servicios en algunos inmuebles: así evita que el
> inquilino retrase el pago y le corten el servicio a todo el edificio, o que deje una deuda al irse.

## 2.2 Conceptos y entidades (modelo conceptual preliminar)

### Negocio / Unidad de negocio
- El inmobiliario es **un negocio** dentro del sistema, que admite N negocios.
- Tiene un **objetivo mensual** de ingresos para el tablero (por ejemplo, objetivo 120 frente a real 116).

### Inmueble / Edificio (propiedad)
- Nombre, dirección y distrito.
- **Valor de adquisición o construcción** y **fecha** (año base para la UIT).
- **Valor actualizado** (calculado: UIT + mejoras; ver 06).
- Medidores o **suministros** generales de agua y luz (puede haber **más de uno**; el cliente suma dos suministros de luz).
- Modalidad de servicios: **el dueño paga y prorratea** o **el inquilino paga directo**. [INFERIDO: por inmueble o por departamento]

### Departamento (unidad alquilable)
- Código (**sin estándar fijo**: "1A", "2B", "501"…), piso e inmueble al que pertenece.
- **Valor** del departamento [PREGUNTA P10: ¿el valor se lleva por edificio, por departamento o por ambos?].
- **Submedidores** propios de agua y luz (con su número de suministro si existe).
- Estado: ocupado o libre.
- Historial de inquilinos.

### Inquilino
- Nombre completo, **DNI** (y **copia escaneada del DNI**), teléfono (el mismo del grupo de WhatsApp), correo y **fecha de nacimiento** (para el saludo de cumpleaños).
- **Datos laborales**: empresa (razón social), RUC [INFERIDO], dirección del centro de trabajo y la **boleta de pago** como documento. *Uso: si hay juicio de desalojo, la notificación va al centro de trabajo.*
- **Historial**: períodos en que vivió en qué departamento (los inquilinos se van y **vuelven**), atrasos y deudas.
- **Calificación** (semáforo verde, amarillo o rojo) basada en su comportamiento de pago.

### Contrato de alquiler
- Inquilino ↔ departamento, fecha de inicio y de fin, **día de pago**, **monto del alquiler**.
- Conceptos adicionales (mantenimiento, limpieza, servicios incluidos o no).
- **Alerta de renovación** antes de que venza.
- **Monto vigente por período** (historial; los montos **no se editan ni se borran**, se agrega uno nuevo).
- **Incrementos programados**: un nuevo monto que rige desde una fecha futura (el cliente lo define con unos 3 meses de anticipación).

> Relación: un departamento tiene muchos inquilinos a lo largo del tiempo, y un inquilino puede
> tener varios contratos (si regresa o cambia de departamento). Se modela como **N:M a través de Contrato**.
> [PREGUNTA P11: ¿puede haber varios inquilinos (co-arrendatarios) en el mismo contrato?]

### Cuota / Obligación de pago (lo que hay que cobrar)
- Generada automáticamente cada mes por contrato: concepto (alquiler, agua, luz, mantenimiento, limpieza, multa por limpieza…), período, monto y fecha de vencimiento.
- Estado: pendiente → pagada (con voucher verificado) / vencida / con atraso de N días.

### Pago y voucher
- Fecha, monto, medio (**Yape**, Plin [INFERIDO], **transferencia**, efectivo [PREGUNTA P12]) y la cuota o cuotas que cubre.
- **Imagen o PDF del voucher**, asociada a **inquilino + departamento + período** (por ejemplo, "enero 2026").
- **Verificación humana**: el sistema **no interpreta** la imagen; una persona confirma que el monto y el período coinciden.
- Hoy los vouchers llegan por **WhatsApp**, y el analista los descarga y los sube al sistema.

### Recibo de servicio (agua y luz)
- Recibo del proveedor (Sedapal / Enel o Luz del Sur [INFERIDO]) por suministro: período, monto total, consumo total y archivo del recibo.
- **Lecturas** de submedidor por departamento: lectura anterior y lectura actual (con **foto** como evidencia).
- Resultado: **monto por departamento** y un **resumen o recibo interno** que se envía a cada inquilino por correo.

### Gasto de mantenimiento común
- Ascensor, energía de áreas comunes, limpieza, vigilancia (por ejemplo, 3 vigilantes en turnos de 8 h para cubrir 24/7).
- Se cobra a los ocupantes como **cuota de mantenimiento** (ejemplo: S/ 185).
- Lo **solicita el analista** y lo **aprueba el dueño** (mensaje "está pendiente su aprobación de gasto por mantenimiento").

### Mejora (inversión en el inmueble)
- Cambio de pisos, ventanas, etc. Tiene fecha, descripción, monto y comprobantes.
- **Siempre se suma** al costo o valor del inmueble (ejemplo: pisos de S/ 50 000).

### Rol de limpieza
- Programación por fechas: qué departamento limpia las áreas comunes en cada período (por ejemplo, del 19 al 24).
- El inquilino envía **fotos** como evidencia, y el dueño o el analista marca el resultado.
- Si el inquilino no puede o no quiere, se contrata a una persona y **se le cobra** (ejemplo: S/ 40).
- Estados propuestos: *Programado → Reportado (con fotos) → Cumplido / Observado / Incumplido → Reemplazado (cobrado)*.

### Cierre de mes
- Candado por período ("octubre 2026 está cerrado"). Ver regla en 06.

## 2.3 Información que hoy maneja en Excel (a migrar)

- Nombre, DNI, fecha de pago, monto a cobrar (alquiler).
- Tabla de servicios: departamento, número de suministro, lectura anterior, lectura actual, consumo, factor (por ejemplo, 0.87) y monto.
- Totales por departamento: agua, luz, mantenimiento y total a pagar.

> **Acción:** pedir al cliente sus Excel reales (anonimizados si lo prefiere) para validar campos. [PREGUNTA P02]

## 2.4 Datos de ejemplo de la reunión (referencia, no reales)

| Dato | Valor |
|------|-------|
| Valor de un inmueble | S/ 500 000 (comprado terminado); construyendo baja a unos S/ 300 000 |
| Alquiler | S/ 2 500 / mes |
| Impuestos anuales | unos S/ 2 000 |
| Mejora de pisos | S/ 50 000 |
| Mantenimiento | S/ 185 |
| Limpieza por reemplazo | S/ 40 |
| Paquete con todo incluido (Jesús María) | S/ 284–300 |
| Recibo de luz de un edificio | unos S/ 524 entre todos |
| Incremento de alquiler | S/ 2 000 → S/ 2 200 |
