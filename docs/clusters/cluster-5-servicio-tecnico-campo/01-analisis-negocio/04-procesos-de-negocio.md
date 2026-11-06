# 04. Procesos de negocio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 4.1 Procesos comunes

### C5-P-01. Recepción del bien
**AS-IS:** papel o memoria; no hay evidencia del estado.
**TO-BE:** se busca por placa o serie, se muestra el historial, se registra motivo, fotos y estado. El cliente firma y recibe su número de orden.

### C5-P-02. Diagnóstico y presupuesto
1. El técnico diagnostica.
2. Se arma el presupuesto (mano de obra + repuestos) y se envía al cliente.
3. El cliente aprueba o rechaza por un enlace o de forma presencial. **Sin aprobación no se ejecuta.**
4. Si aparece algo nuevo, se pide una aprobación adicional.

### C5-P-03. Ejecución
Se asigna técnico y bahía. Los repuestos se reservan y luego se descuentan de stock. Se registran las horas.

### C5-P-04. Control de calidad, entrega y cobro
Revisión final → Cliente recibe aviso → Cobro → Entrega con conformidad → Empieza la garantía.

### C5-P-05. Consulta de estado
El cliente consulta con un enlace seguro, sin crear cuenta: *En revisión → Esperando repuesto → Presupuesto pendiente → Listo para retirar*.

### C5-P-06. Reclamo por garantía
Se abre una OT vinculada a la original. Si procede, no se cobra y su costo se imputa como costo de garantía.

## 4.2 Procesos por vertical

### C5-P-10. Mantenimiento por kilometraje (5.1) [MAPEO]
Con el kilometraje y la fecha de cada visita se estima el uso, y se avisa cuando se acerca el próximo cambio.

### C5-P-11. Trabajo por siniestro (5.1) [MAPEO]
La aseguradora autoriza; se le cobra lo cubierto y al cliente el deducible. Son dos obligaciones de la misma OT.

### C5-P-20. Tarifa de diagnóstico (5.2) [MAPEO]
Se cobra por adelantado. Si el cliente aprueba la reparación, se descuenta; si no, se queda como ingreso.

### C5-P-21. Equipos abandonados (5.2) [MAPEO]
Si el equipo está listo y nadie lo retira, se envían avisos escalonados. Vencido el plazo, pasa a *Abandonado* según la política acordada y su validez legal.

### C5-P-30. Contrato de abono (5.3) [MAPEO]
1. Se pactan frecuencia, alcance y precio.
2. El sistema genera las OT del período y la obligación de cobro mensual.
3. Se facturan juntos abonos y servicios extraordinarios.

### C5-P-31. Planificación de rutas y cuadrillas (5.3) [MAPEO]
Se agrupan las OT del día por zona y se asignan a una cuadrilla. El supervisor la sigue desde su celular.

### C5-P-32. Certificado de servicio (5.3) [MAPEO]
Al terminar, el técnico registra fotos y datos, el cliente firma en sitio y el sistema emite el certificado en PDF.

### C5-P-33. Entrega de insumos y uniformes (5.3) [MAPEO]
Se registra lo que recibe cada trabajador. Los químicos consumidos se cargan a la OT o contrato.
