# 06. Requerimientos preliminares

> Borrador para el SRS del clúster. Prioridad **MoSCoW**. La columna **Etapa** remite a [07-fases-y-alcance.md](07-fases-y-alcance.md).
> Los requerimientos transversales están en [el documento general](../../../general/01-analisis-negocio/06-requerimientos-preliminares.md).

## 6.1 Vertical piloto

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| C1-RF-20 | Registrar inmuebles (dirección, valor base, año base, suministros, modalidad de servicios) | M | 1 |
| C1-RF-21 | Registrar unidades (departamentos, puestos de mercado, cocheras) con tipo, código libre, piso y submedidores (ver C1-RF-60) | M | 1 |
| C1-RF-22 | Registrar inquilinos: nombre, DNI, teléfono, correo, fecha de nacimiento, datos laborales | M | 1 |
| C1-RF-23 | Adjuntar al inquilino la copia del DNI y la boleta de pago | M | 1 |
| C1-RF-24 | Registrar contratos (inquilino, departamento, fechas, día de pago, monto, conceptos) | M | 1 |
| C1-RF-25 | Generar automáticamente las **cuotas mensuales** de cada contrato | M | 1 |
| C1-RF-26 | Mantener el **historial de montos** por contrato (no editar ni borrar; nueva fila con vigencia) | M | 1 |
| C1-RF-27 | **Programar incrementos** de alquiler con fecha futura | M | 1 |
| C1-RF-28 | Registrar pagos y **subir el voucher**, asociado a inquilino, departamento, período y concepto | M | 1 |
| C1-RF-29 | **Verificar** el voucher (confirmación humana) y marcar la cuota como pagada | M | 1 |
| C1-RF-30 | Advertir si se sube un **archivo idéntico** a uno ya existente (comparando hash) | S | 1 |
| C1-RF-31 | Consultar los vouchers por inquilino y período ("muéstrame todos los vouchers de 2026") | M | 1 |
| C1-RF-32 | Lista **semanal** de cobros y lista de "hoy vence" para el analista | M | 1 |
| C1-RF-33 | Alerta al dueño por atraso ≥ N días (configurable, 7 por defecto) por **correo electrónico y bandeja del sistema** *(segundo nivel del escalamiento de C1-RF-57)* [CONFIRMADO — P7] | M | 1 |
| C1-RF-34 | Alerta de **renovación de contrato** X días antes de su vencimiento | M | 1 |
| C1-RF-35 | Historial del inquilino: estadías, atrasos y deudas (incluye inquilinos que regresan) | M | 1 |
| C1-RF-36 | **Calificación** del inquilino (verde, amarillo o rojo) con criterios ponderados configurables | S | 2 |
| C1-RF-37 | Registrar recibos de agua, luz y gas del proveedor (uno o más suministros) con su archivo | M | 2 |
| C1-RF-38 | Registrar lecturas de submedidores con foto; la lectura anterior se toma del mes previo | M | 2 |
| C1-RF-39 | **Calcular el prorrateo** por departamento, **proporcional al consumo** y **por suministro**, con cuadre exacto al total de cada recibo (agua y alcantarillado, luz y gas) [CONFIRMADO — P10] | M | 2 |
| C1-RF-40 | Generar el **resumen de servicios** por inquilino y enviarlo por correo con los adjuntos | S | 2 |
| C1-RF-41 | Registrar si el dueño ya pagó el recibo al proveedor | S | 2 |
| C1-RF-42 | Registrar gastos de mantenimiento con el flujo **solicitud → aprobación del dueño** | S | 2 |
| C1-RF-43 | **Rol de limpieza**: cronograma, evidencia fotográfica, estados y cargo por reemplazo | S | 2 |
| C1-RF-44 | Registrar **mejoras** que se suman al costo del inmueble | M | 2 |
| C1-RF-45 | Calcular el **valor actualizado** del inmueble con la UIT (más mejoras) | M | 2 |
| C1-RF-46 | Calcular el **rendimiento** mensual y anual, los años de recuperación y la comparación con un plazo fijo, por inmueble y total | M | 2 |
| C1-RF-47 | **Cierre de mes** con validaciones (sin deudas, vouchers completos, servicios pagados) y bloqueo de cambios | S | 2 |
| C1-RF-48 | Saludo automático de **cumpleaños** por correo | C | 2 |
| C1-RF-49 | Exportar reportes (cobranza, morosidad, rendimiento) a Excel o PDF (ver C1-RF-56) | S | 2 |
| C1-RF-50 | Importar los datos iniciales desde los Excel actuales del cliente | S | 1 |
| C1-RF-51 | Armar el **dossier de desalojo** con contrato, datos laborales, deuda y comprobantes | S | 2 |
| C1-RF-52 | Emitir el **desglose en PDF** del estado de cuenta por correo | S | 2 |
| C1-RF-53 | Declarar una cuota como **incobrable**, con autorización y motivo | S | 2 |
| C1-RF-54 | Comparar el Cap Rate con la tasa del módulo de inversiones, o con una tasa manual si no está activo | S | 2 |
| C1-RF-55 | Guardar el **autovalúo** (impuesto predial) de cada inmueble por año, con su archivo y fecha de pago [CONFIRMADO — PPT cliente] | M | 1 |
| C1-RF-56 | **Vista tipo tabla (estilo Excel)** de cuotas por contrato: período, monto, fecha de vencimiento, fecha de pago, estado, y una **columna de incremento programado** visible; filtrable, ordenable y exportable [CONFIRMADO — PPT cliente] | M | 1 |
| C1-RF-57 | **Escalamiento de alerta por falta de pago:** primero al **analista**; si no se regulariza en N días (configurable), al **dueño/gerente** [CONFIRMADO — PPT cliente] | M | 1 |
| C1-RF-58 | Prorratear y cobrar el **gas** igual que agua y luz, cuando el inmueble lo tenga [CONFIRMADO — PPT cliente] | S | 2 |
| C1-RF-59 | Registrar **pagos parciales** de una cuota (varios pagos, cada uno con su voucher), mostrar el **saldo pendiente** y el estado *Pago parcial*, **sin** calcular intereses ni penalidad [CONFIRMADO — P8] | M | 1 |
| C1-RF-60 | Catálogo configurable de **tipos de unidad** (departamento, puesto o local de mercado, cochera), cada uno con sus atributos y conceptos de cobro [CONFIRMADO — P5] | M | 1 |
| C1-RF-61 | Asociar cada submedidor a un **suministro** del inmueble, para prorratear cada recibo solo entre sus departamentos [CONFIRMADO — P10] | M | 2 |
| C1-RF-62 | Indicador de **ocupación** (unidades ocupadas / alquilables) en la tarjeta del tablero, junto al monto cobrado, con la lista de unidades libres [CONFIRMADO — P6] | S | 2 |
| C1-RF-63 | Ocultar **sumas y subtotales** en todas las listas, exportaciones y reportes que vea el analista (lista semanal sin fila de total) [CONFIRMADO — P9, NUC-RN-30] | M | 1 |
| C1-RF-83 | **Portal o app para el inquilino**: ver su deuda, subir comprobantes y reportar limpieza | C | 3 |

## 6.2 Demás verticales [INFERIDO a partir del mapeo]

Se implementan cuando llegue un cliente de esa vertical.

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C1-RF-100 | Calendario de ocupación por unidad | Todas | M |
| C1-RF-101 | Registrar garantías y depósitos como dinero de terceros | Todas | M |
| C1-RF-102 | Tickets de mantenimiento o siniestro con costo por unidad | Todas | S |
| C1-RF-110 | Catálogo con ficha, galería, propietario y estado | 1.1 | M |
| C1-RF-111 | Pipeline de comercialización | 1.1 | S |
| C1-RF-112 | Penalidad por mora y ajuste por IPC configurables | 1.1 | S |
| C1-RF-113 | Liquidación a propietarios y comisiones de agentes | 1.1 | M |
| C1-RF-120 | Padrón de unidades con alícuota | 1.2 | M |
| C1-RF-121 | Emisión masiva de recibos y estado de cuenta por residente | 1.2 | M |
| C1-RF-122 | Reserva de áreas comunes | 1.2 | S |
| C1-RF-123 | Fondo de reserva y bitácora de mantenimiento preventivo | 1.2 | S |
| C1-RF-130 | Ficha con kilometraje u horómetro, seguros y revisiones, con alertas | 1.3 | M |
| C1-RF-131 | Tarifario por hora, día, semana y mes, con kilometraje incluido y excesos | 1.3 | M |
| C1-RF-132 | Actas digitales de entrega y devolución con fotos | 1.3 | M |
| C1-RF-133 | Cargos adicionales: combustible, multas y daños | 1.3 | S |
| C1-RF-140 | Mapa lógico de espacios | 1.4 | M |
| C1-RF-141 | Membresías recurrentes con créditos | 1.4 | M |
| C1-RF-142 | Reserva de salas con consumo de créditos | 1.4 | S |
| C1-RF-143 | Servicios adicionales (paquetería, domicilio fiscal) y métrica por m² | 1.4 | C |

## 6.3 Requerimientos no funcionales propios

| ID | Requerimiento |
|----|---------------|
| C1-RNF-01 | Los datos laborales, DNI y boletas de pago se tratan como información restringida; requieren el consentimiento del inquilino (Ley 29733) |
| C1-RNF-02 | Las fotos de medidores y actas se pueden cargar desde el celular y tienen fecha de captura |
| C1-RNF-03 | Los cálculos de prorrateo tienen pruebas automáticas de cuadre exacto |
