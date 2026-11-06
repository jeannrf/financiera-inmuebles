# 04. Procesos de negocio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 4.1 Procesos comunes

### C2-P-01. Captación y calificación
**AS-IS:** los contactos llegan por WhatsApp o referidos, y cada vendedor los anota a su modo.
**TO-BE:**
1. Se registra el lead con su origen y se asigna a un vendedor.
2. El sistema detecta si el contacto ya existe.
3. El vendedor lo califica y avanza la oportunidad por el pipeline.
4. Si una oportunidad lleva N días sin actividad, se alerta al vendedor y luego al gerente.

### C2-P-02. Cotización versionada
1. El vendedor arma la cotización con líneas de costo y precio.
2. Si el descuento o margen excede el límite, se pide aprobación del dueño.
3. Se genera el PDF y se envía al cliente.
4. Cada cambio crea una **versión nueva**; las anteriores no se alteran.

### C2-P-03. Cierre
1. El cliente acepta una versión.
2. Se crea el contrato, la póliza o el pedido, y se congela el precio.
3. Se genera el plan de pagos y las tareas de trámite.
4. La oportunidad pasa a *Ganada*; si se pierde, se registra el motivo.

### C2-P-04. Cobro fraccionado
Usa el flujo de obligaciones del núcleo (cuota o hito → pago → comprobante → alertas de atraso).

### C2-P-05. Liquidación de comisiones
1. Un evento (venta, cobro o pago de aseguradora) genera la comisión según reglas por rol.
2. Al cierre del período, se consolida por beneficiario.
3. El dueño aprueba y se registra el pago. Si se anula una venta, se genera un ajuste en contra (nunca se edita la liquidación).

### C2-P-06. Forecast mensual
El sistema calcula los ingresos esperados según etapa y probabilidad, y los compara con el objetivo del tablero.

## 4.2 Procesos por vertical

### C2-P-10. Renovación de pólizas (2.1) [MAPEO]
1. Una póliza activa genera una oportunidad de renovación con alertas a los **60, 30 y 15 días**.
2. Corre en un pipeline paralelo, y si no se gestiona escala al gerente.

### C2-P-11. Siniestros (2.1) [MAPEO]
Recepción del reclamo → Peritaje → Liquidación de la aseguradora, con documentos y plazos.

### C2-P-12. Conciliación de comisiones de aseguradoras (2.1) [MAPEO]
Se compara la comisión esperada con la que paga cada aseguradora, y se calcula lo cedido a sub-agentes.

### C2-P-20. Alistamiento de vehículo (2.2) [MAPEO]
Cada gasto (chapa, pintura, trámites) se imputa al vehículo y aumenta su costo antes de la venta.

### C2-P-21. Retoma (2.2) [MAPEO]
1. Se tasa el vehículo del cliente.
2. El valor se aplica como parte de pago.
3. El vehículo entra al inventario con costo igual a la tasación aprobada, y se alista para la venta.

### C2-P-22. Consignación (2.2) [MAPEO]
El vehículo no es del negocio. Al venderlo, se liquida al dueño original el precio menos la comisión pactada y los gastos autorizados.

### C2-P-30. Del lead a la instalación (2.3) [MAPEO]
Lead → Visita técnica → Dimensionamiento y presupuesto → Aprobación → Ejecución. Al terminar se activa el contrato de mantenimiento anual, que puede operar con el Clúster 5.

### C2-P-40. Reservas y pagos a proveedores (2.4) [MAPEO]
1. Se arma el itinerario y los pasajeros con sus documentos.
2. Se confirma cada servicio y se guarda la confirmación del proveedor.
3. El sistema cruza lo cobrado al cliente con las **fechas límite de pago a proveedores**, y alerta los riesgos.
4. Las salidas grupales controlan cupos bloqueados.
