# 04. Procesos de negocio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 4.1 Procesos comunes

### C3-P-01. Alta de cliente y apertura de proyecto
**AS-IS:** carpetas, Excel y correos dispersos.
**TO-BE:** se crea la cuenta, se elige iguala o proyecto, se asignan responsables y se abre el centro de costo.

### C3-P-02. Iguala mensual
1. Se define el honorario fijo y los entregables comprometidos.
2. El motor de cobro recurrente genera la obligación mensual (reutiliza el motor del piloto).
3. Cada mes se revisan entregables y horas consumidas frente a lo pagado.

### C3-P-03. Proyecto cerrado por hitos
1. Se planifican hitos con su monto y fecha.
2. Al completar un hito, el cliente lo aprueba y se genera la obligación de cobro.
3. El sistema alerta hitos cumplidos y aún no facturados.

### C3-P-04. Registro de horas
Cada profesional imputa horas a una tarea; se valorizan con su costo hora. El sistema recuerda a quien no ha registrado y el jefe aprueba.

### C3-P-05. Gastos reembolsables
1. Se registra el gasto con su comprobante, marcado como **por cuenta del cliente**.
2. Se guarda como dinero de terceros, fuera del P&L.
3. Se reembolsa aparte de los honorarios y se concilia.

### C3-P-06. Análisis de rentabilidad
El sistema consolida ingresos, horas valorizadas y subcontrataciones, y los muestra por proyecto y cliente.

## 4.2 Procesos por vertical

### C3-P-10. Vencimientos procesales y tributarios (3.1) [MAPEO]
Línea de tiempo de actuaciones con alertas escalonadas. Un vencimiento sin responsable o sin atender se escala al socio.

### C3-P-20. Servicio recurrente con entregables mensuales (3.2) [MAPEO]
Se comprometen entregables por mes, se controla su cumplimiento y se separa el presupuesto de pauta del fee de agencia.

### C3-P-30. Presupuesto de obra (3.3) [MAPEO]
Se estructura en partidas y rubros, el cliente lo aprueba y esa versión queda como línea base.

### C3-P-31. Certificación de avance (3.3) [MAPEO]
1. El residente registra el avance físico por partida.
2. El sistema calcula lo certificable, menos lo anterior y las retenciones.
3. El cliente aprueba y se genera la obligación de cobro.

### C3-P-32. Adicionales (Change Orders) (3.3) [MAPEO]
1. Se detecta trabajo no presupuestado y se cotiza.
2. El cliente aprueba **antes** de ejecutarlo.
3. Aumenta el presupuesto vigente, sin alterar la línea base.

### C3-P-33. Compras y subcontratos a obra (3.3) [MAPEO]
Órdenes de compra y destajos se imputan a una partida; el sistema alerta si se supera lo presupuestado.

### C3-P-40. Búsqueda de personal (3.4) [MAPEO]
1. Se abre la vacante con su perfil y condiciones, y se cobra el anticipo.
2. Pipeline: Filtro CV → Entrevista → Pruebas → Terna presentada → Contratado.
3. Al contratar, se cobra el cierre y empieza el período de garantía con alerta (por ejemplo, 3 meses).
