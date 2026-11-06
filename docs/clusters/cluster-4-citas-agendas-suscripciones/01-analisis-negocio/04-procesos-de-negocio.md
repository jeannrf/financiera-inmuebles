# 04. Procesos de negocio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 4.1 Procesos comunes

### C4-P-01. Alta de la persona atendida
Se busca por documento o teléfono en la organización; se registra con su responsable de pago y, si aplica, el consentimiento de datos.

### C4-P-02. Reserva de cita o clase
**AS-IS:** llamadas y WhatsApp, anotadas en un cuaderno.
**TO-BE:**
1. Recepción o la propia persona elige servicio, profesional y horario.
2. El sistema valida disponibilidad del profesional, del recurso y del cupo.
3. Envía confirmación y un recordatorio antes de la cita.

### C4-P-03. Recepción y atención
Estados: *Confirmada → En sala de espera → Atendido* o *No asistió*.
Al marcar *Atendido*: se descuenta el saldo del paquete, se registran insumos y se genera la comisión.

### C4-P-04. Venta y consumo de paquetes
1. Se vende el paquete y se cobra por adelantado (total o en cuotas).
2. El ingreso queda **diferido**.
3. Cada atención descuenta 1 sesión y reconoce el ingreso proporcional.
4. Se alerta cuando queda poco saldo o está por vencer.

### C4-P-05. Membresías: renovación y congelamiento
1. El motor de cobro recurrente genera la obligación del período.
2. Se alerta la renovación; si no renueva, pasa a *Vencida* y se registra como posible baja.
3. Un socio puede congelar días por viaje o lesión, y la vigencia se extiende.

### C4-P-06. Caja diaria
1. Cada venta se registra con su método de pago.
2. Al cierre, el cajero declara lo contado y el sistema calcula la diferencia.
3. Una diferencia sobre el umbral alerta al dueño. La caja cerrada no se edita.

### C4-P-07. Liquidación de honorarios
Al cierre del período, el sistema suma por profesional las atenciones, aplica su regla y descuenta insumos o laboratorio. El dueño aprueba.

## 4.2 Procesos por vertical

### C4-P-10. Consentimiento e historial clínico (4.1) [MAPEO]
Consentimiento firmado, evolución por atención, odontograma o esquema corporal y fotos de antes y después. Toda nota es de solo adición.

### C4-P-11. Presupuesto financiado (4.1) [MAPEO]
Se presenta el plan de tratamiento, se aprueba y se genera el plan de cuotas.

### C4-P-20. Matrícula y ciclo lectivo (4.2) [MAPEO]
Se abren ciclos, cursos y horarios con aula, profesor y cupo. Se matricula al alumno, se cobra y se generan las pensiones. Se registra la asistencia.

### C4-P-21. Control de morosidad de pensiones (4.2) [MAPEO]
Reutiliza las alertas del núcleo. Las consecuencias para el alumno son una política a validar legalmente.

### C4-P-30. Clases con cupo limitado (4.3) [MAPEO]
El socio reserva un lugar; al llenarse, entra a lista de espera. Si cancela tarde o no asiste, se aplica la política configurada.

### C4-P-40. Medicina preventiva (4.4) [MAPEO]
El motor recuerda vacunas, desparasitaciones y controles por mascota según su especie y edad, por WhatsApp o correo.

### C4-P-41. Ticket híbrido (4.4) [MAPEO]
Un solo ticket une consulta, medicamentos y productos de Pet Shop.
