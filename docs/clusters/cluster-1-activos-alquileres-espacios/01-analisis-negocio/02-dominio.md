# 02. Dominio

## 2.1 Modelo común del clúster [INFERIDO]

Las 4 verticales comparten esta forma; solo cambian nombres y atributos.

```
Activo o agrupador (Edificio, Sede, Flota)
└── Unidad (Departamento, Vehículo, Escritorio)
     ├── Contrato ── Contraparte (Inquilino, Conductor, Miembro)
     │    ├── Tarifa con vigencia
     │    ├── Garantía o depósito
     │    └── Obligaciones → Pagos → Comprobantes
     ├── Calendario de ocupación
     ├── Tickets de mantenimiento
     └── Centro de costo
```

| Concepto común | 1.1 Inmobiliaria | 1.2 Edificios | 1.3 Flotas | 1.4 Coworking y storage |
|----------------|------------------|---------------|------------|-------------------------|
| **Unidad** | Inmueble, departamento | Departamento, local | Vehículo, máquina | Oficina, escritorio, bodega |
| **Contraparte** | Inquilino | Residente, propietario | Conductor, empresa | Miembro |
| **Periodicidad** | Mensual | Mensual | Hora, día, semana, mes | Mensual, pase |
| **Medición** | Submedidores | Lecturas, alícuota | Km, horómetro | Créditos, m², m³ |
| **Gasto repartido** | Agua, luz, mantenimiento | Gastos comunes, fondo de reserva | No aplica | Servicios adicionales |
| **Evidencia clave** | Voucher, foto del medidor | Recibo, lectura | Acta con fotos | Control de acceso |

## 2.2 Especificación por vertical (del mapeo)

*Basado en la arquitectura del vertical Inmobiliario: Control de unidades físicas, contratos de uso temporal, disponibilidad y rentabilidad por unidad.*

### Arquitectura del clúster
* **Entidad Principal:** Activo / Unidad (Propiedad, Vehículo, Oficina, Maquinaria, Bodega).
* **Sub-entidades:** Contratos de arrendamiento/alquiler, Calendario de ocupación, Tickets de mantenimiento/siniestros, Garantías/Depósitos.
* **Conexión Financiera (P&L):** Centro de costo por unidad individual (permite saber cuánto rinde exactamente el "Departamento 402" o la "Excavadora CAT-01" descontando sus gastos de mantenimiento).

### Verticales

#### 1.1. Inmobiliarias y Administración de Propiedades (Property Management)
* **Cobertura Operativa:**
  * Catálogo de inmuebles con ficha técnica, galería, propietario asignado y estado (Disponible, Reservado, Alquilado, En Venta, En Mantenimiento).
  * Pipeline de comercialización (Visitas agendadas → Oferta/Reserva → Evaluación crediticia → Firma de contrato).
  * Gestión de alquileres: Generación recurrente de cuotas mensuales, cálculo automático de penalidades por mora, ajustes por inflación/IPC y alertas de vencimiento de contrato.
* **Cobertura Financiera:** Liquidación a propietarios (Cobro de alquiler menos comisión de administración y gastos de reparación = Monto a transferir al dueño), control de depósitos en garantía y comisiones de agentes inmobiliarios.

#### 1.2. Administración de Edificios, Condominios y Centros Comerciales
* **Cobertura Operativa:**
  * Padrón de unidades (departamentos/locales) con porcentaje de participación o alícuota de gastos comunes.
  * Registro de lecturas de consumos individuales (agua, luz, gas) y prorrateo de gastos generales del edificio (seguridad, limpieza, ascensores).
  * Calendario de reserva de áreas comunes (SUM, parrillas, salas) y bitácora de mantenimiento preventivo de instalaciones.
* **Cobertura Financiera:** Emisión masiva de recibos de mantenimiento mensual, estado de cuenta por residente, control de fondo de reserva y reporte de morosidad del edificio.

#### 1.3. Rent-a-Car y Alquiler de Flotas / Maquinaria / Equipos
* **Cobertura Operativa:**
  * Ficha de unidad con control de kilometraje/horómetro, vencimiento de seguros, revisiones técnicas y estado en tiempo real (En patio, Alquilado, En taller).
  * Tarifario flexible (por hora, día, semana o mes) con paquetes de kilometraje incluido y cargos por exceso.
  * Acta digital de Entrega y Devolución (Check-in / Check-out) con registro fotográfico de daños, nivel de combustible y accesorios entregados.
* **Cobertura Financiera:** Bloqueo/registro de garantías, facturación de adicionales (combustible, multas de tránsito, daños), costo de mantenimiento preventivo/correctivo por vehículo y cálculo de ROI por unidad de la flota.

#### 1.4. Coworkings, Centros de Negocios y Self-Storage (Mini-bodegas)
* **Cobertura Operativa:**
  * Mapa lógico de espacios: Oficinas privadas, escritorios fijos, pases flexibles y salas de reuniones (o metros cúbicos en caso de bodegas).
  * Gestión de membresías recurrentes con asignación de créditos u horas mensuales para uso de salas de reuniones o impresiones.
  * Control de accesos/ocupación y servicios adicionales (recepción de paquetería, domicilio fiscal, cafetería).
* **Cobertura Financiera:** Facturación recurrente automática el día 1 de cada mes, cobro de consumos extras y métrica de ingresos por metro cuadrado (Ingreso / m²).

## 2.3 Vertical piloto: alquiler directo de departamentos

El cliente piloto opera entre 1.1 y 1.2, con una diferencia importante: **es el propietario**, de modo que no aplica la liquidación
a propietarios terceros. Las cifras y zonas concretas están en su [configuración](../../../clientes/cliente-piloto/03-configuracion-y-datos.md).

El cliente **construye** edificios (es lo más barato; también compra en planos o terminado) y **alquila** los departamentos. Los
ingresos vienen del **alquiler mensual** y además se cobran (o se trasladan) **servicios**: agua, luz, gas, mantenimiento de áreas
comunes y limpieza. Hay dos modalidades: **el dueño paga y prorratea** o **el inquilino paga directamente o paga un paquete con todo incluido**.

#### Negocio / Unidad de negocio
- El inmobiliario es **un negocio** dentro del sistema, que admite N negocios.
- Tiene un **objetivo mensual** de ingresos para el tablero (por ejemplo, objetivo 120 frente a real 116). El monto real son
  los ingresos **efectivamente cobrados**, y la meta de fondo es la **ocupación total** [CONFIRMADO — P6; ver [B8](05-reglas-de-negocio-y-calculos.md#b8-indicadores-del-tablero-cobranza-y-ocupación)].

#### Inmueble / Edificio (propiedad)
- Nombre, dirección y distrito.
- **Valor de adquisición o construcción** y **fecha** (año base para la UIT).
- **Valor actualizado** (calculado: UIT + mejoras; ver `05-reglas-de-negocio-y-calculos.md`). *Desde P11 es solo referencia [C1-Q-62].*
- **Año de construcción**, para calcular la **antigüedad** y la depreciación de 1 % por año [CONFIRMADO — P11].
- **Zona** a la que pertenece, para usar el estudio de mercado que le corresponde [CONFIRMADO — P11].
- Medidores o **suministros** generales de agua y luz (puede haber **más de uno**; el cliente suma dos suministros de luz).
- Modalidad de servicios: **el dueño paga y prorratea** o **el inquilino paga directo**. [INFERIDO: por inmueble o por departamento]

#### Unidad alquilable (departamento, puesto de mercado o cochera)
- **Tipo de unidad** [CONFIRMADO — cuestionario P5]: el piloto alquila **departamentos**, unidades en un **mercado** (puesto o
  local [INFERIDO → C1-Q-58]) y **cocheras**. El tipo es un **catálogo configurable**, no una lista fija en el código (NUC-RN-25).
  Cada tipo define qué atributos y conceptos usa:

  | Tipo | Submedidores | Servicios prorrateados | Mantenimiento y limpieza |
  |------|:------------:|:----------------------:|:------------------------:|
  | Departamento | Agua y luz | Sí (si el dueño paga el recibo) | Sí |
  | Puesto o local de mercado | [PREGUNTA C1-Q-58] | [PREGUNTA C1-Q-58] | [PREGUNTA C1-Q-58] |
  | Cochera | No [INFERIDO] | No [INFERIDO] | [PREGUNTA C1-Q-58] |

- Código (**sin estándar fijo**: "1A", "2B", "501", "C-03"…), piso (si aplica) e inmueble al que pertenece.
- **Área en m²** [CONFIRMADO — P11]: es la base del alquiler sugerido y del rendimiento por m².
- **Valor** de la unidad: con P11 se obtiene **por unidad** (área × valor por m² depreciado), sin repartir el valor del edificio [INFERIDO → C1-Q-10].
- **Submedidores** propios de agua y luz (con su número de suministro si existe). Cada submedidor de luz pertenece a **un
  suministro** del inmueble; dos departamentos del mismo edificio pueden estar en suministros distintos [CONFIRMADO — P10].
- Estado: **ocupada o libre**. Es la base del indicador de **ocupación** del tablero (la meta del dueño es que ninguna quede libre).
- Historial de inquilinos.

> Volumen actual del piloto: **11 unidades** y **1 analista** ([configuración](../../../clientes/cliente-piloto/03-configuracion-y-datos.md#34-dimensionamiento-actual)).

#### Estudio de mercado por zona [CONFIRMADO — P11]
- **Zona** (distrito o sector), **fecha** del estudio y quién lo hizo (el analista) y lo validó (el dueño).
- **Comparables**: avisos de **alquiler** y de **venta de departamentos nuevos**, cada uno con fuente (portal o enlace), área en m², precio y tipo de unidad.
- Resultados: **alquiler promedio por m²** y **precio nuevo promedio por m²** de la zona. Se guardan con fecha de vigencia
  (NUC-RN-01), para que el rendimiento de meses pasados no cambie al hacer un estudio nuevo.

#### Inquilino
- Nombre completo, **DNI** (y **copia escaneada del DNI**), teléfono (el mismo del grupo de WhatsApp), correo y **fecha de nacimiento** (para el saludo de cumpleaños).
- **Datos laborales**: empresa (razón social), RUC [INFERIDO], dirección del centro de trabajo y la **boleta de pago** como documento. *Uso: si hay juicio de desalojo, la notificación va al centro de trabajo.*
- **Historial**: períodos en que vivió en qué departamento (los inquilinos se van y **vuelven**), atrasos y deudas.
- **Calificación** (semáforo verde, amarillo o rojo) basada en su comportamiento de pago.

#### Contrato de alquiler
- Inquilino ↔ departamento, fecha de inicio y de fin, **día de pago**, **monto del alquiler**.
- Conceptos adicionales (mantenimiento, limpieza, servicios incluidos o no).
- **Alerta de renovación** antes de que venza.
- **Monto vigente por período** (historial; los montos **no se editan ni se borran**, se agrega uno nuevo).
- **Incrementos programados**: un nuevo monto que rige desde una fecha futura (el cliente lo define con unos 3 meses de anticipación).

> Relación: un departamento tiene muchos inquilinos a lo largo del tiempo, y un inquilino puede
> tener varios contratos (si regresa o cambia de departamento). Se modela como **N:M a través de Contrato**.
> [PREGUNTA C1-Q-11: ¿puede haber varios inquilinos (co-arrendatarios) en el mismo contrato?]

#### Cuota / Obligación de pago (lo que hay que cobrar)
- Generada automáticamente cada mes por contrato: concepto (alquiler, agua, luz, mantenimiento, limpieza, multa por limpieza…), período, monto y fecha de vencimiento.
- Estado: pendiente → **pago parcial** (con saldo pendiente) → pagada (con voucher verificado) / vencida / morosa (≥ 7 días de atraso).
- **Saldo pendiente** = monto de la cuota − Σ pagos verificados. **Sin intereses ni penalidad por mora** [CONFIRMADO — P8].
- **Acuerdo de pago por partes**: si el inquilino pide pagar por partes antes de los 7 días, se registra (fecha del pedido y
  fechas prometidas) y la cuota **no** pasa a incobrable [CONFIRMADO — P12].
- **Incobrable**: a los 7 días de atraso sin acuerdo, con fecha, motivo y quién lo confirmó. La deuda sigue en el historial [CONFIRMADO — P12].

#### Suspensión de servicios [CONFIRMADO — P12]
- Unidad, servicios suspendidos (**agua** y/o **luz**), fecha, cuota que la motivó y quién la ordenó.
- **Reposición**: fecha y motivo (pago, acuerdo) [PREGUNTA C1-Q-69].
- Mientras dure, la unidad no genera consumo en el prorrateo de ese suministro.

#### Pago y voucher
- Fecha, monto, medio (**Yape**, Plin [INFERIDO], **transferencia**, efectivo [PREGUNTA C1-Q-12]) y la cuota o cuotas que cubre.
- Una cuota puede tener **varios pagos** (pagos parciales), cada uno con **su propio voucher** [CONFIRMADO — P8].
- **Imagen o PDF del voucher**, asociada a **inquilino + departamento + período** (por ejemplo, "enero 2026").
- **Verificación humana**: el sistema **no interpreta** la imagen; una persona confirma que el monto y el período coinciden.
- Hoy los vouchers llegan por **WhatsApp**, y el analista los descarga y los sube al sistema.

#### Recibo de servicio (agua y luz)
- Recibo del proveedor (Sedapal / Enel o Luz del Sur [INFERIDO]) **por suministro**: período, monto total, consumo total y archivo del recibo.
  El recibo de agua incluye **agua y alcantarillado** [CONFIRMADO — P10].
- Cada suministro tiene su **grupo de departamentos**: el recibo se reparte solo entre los departamentos conectados a él.
  Unos departamentos pueden tener un proveedor o suministro de luz distinto al de otros [CONFIRMADO — P10].
- **Lecturas** de submedidor por departamento: lectura anterior (la del mes pasado) y lectura actual (con **foto** como evidencia).
- Resultado: **monto por departamento**, proporcional a su consumo ([B3](05-reglas-de-negocio-y-calculos.md#b3-prorrateo-de-servicios-agua-y-luz)), y un **resumen o recibo interno** que se envía a cada inquilino por correo.

#### Gasto de mantenimiento común
- Ascensor, energía de áreas comunes, limpieza, vigilancia (por ejemplo, 3 vigilantes en turnos de 8 h para cubrir 24/7).
- Se cobra a los ocupantes como **cuota de mantenimiento** (ejemplo: S/ 185).
- Lo **solicita el analista** y lo **aprueba el dueño** (mensaje "está pendiente su aprobación de gasto por mantenimiento").

#### Mejora (inversión en el inmueble)
- Cambio de pisos, ventanas, etc. Tiene fecha, descripción, monto y comprobantes.
- **Siempre se suma** al costo o valor del inmueble (ejemplo: pisos de S/ 50 000).

#### Rol de limpieza
- Programación por fechas: qué departamento limpia las áreas comunes en cada período (por ejemplo, del 19 al 24).
- El inquilino envía **fotos** como evidencia, y el dueño o el analista marca el resultado.
- Si el inquilino no puede o no quiere, se contrata a una persona y **se le cobra** (ejemplo: S/ 40).
- Estados propuestos: *Programado → Reportado (con fotos) → Cumplido / Observado / Incumplido → Reemplazado (cobrado)*.

#### Cierre de mes
- Candado por período ("octubre 2026 está cerrado"). Ver C1-RN y NUC-RN-11 en `05-reglas-de-negocio-y-calculos.md`.
