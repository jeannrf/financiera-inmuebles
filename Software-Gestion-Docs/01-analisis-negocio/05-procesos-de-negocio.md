# 05. Procesos de negocio

Para cada proceso se describe cómo se hace **hoy (AS-IS)** y cómo se haría **con el sistema (TO-BE)**.
Estos procesos son la base de los diagramas de actividades y casos de uso.

---

## P-01. Alta de inmueble y departamentos
**TO-BE**
1. El dueño registra el inmueble (dirección, valor, fecha base, suministros de agua y luz, modalidad de servicios).
2. Registra sus departamentos (código libre, piso, submedidores, valor si aplica).
3. Se guarda el valor base para calcular la valorización por UIT.

## P-02. Alta de inquilino y contrato
**AS-IS:** los datos están en Excel y el teléfono en el grupo de WhatsApp.
**TO-BE**
1. El analista o el dueño registra al inquilino (o lo **busca**, si ya vivió antes, y ve su historial y su calificación).
2. Sube la copia del DNI y la boleta de pago (datos laborales).
3. El dueño crea el contrato: departamento, fechas, día de pago, monto y conceptos incluidos.
4. El sistema programa las cuotas mensuales y la alerta de renovación.

## P-03. Cobro mensual de alquiler (proceso central)
**AS-IS:** el dueño revisa el Excel y el WhatsApp, recibe los vouchers por WhatsApp, los compara a ojo y persigue a los morosos.
**TO-BE**
1. **El sistema** genera la cuota del mes por contrato, con el monto vigente para ese período.
2. Al inicio de la semana, el **analista** recibe la **lista de cobros de la semana**.
3. El día del vencimiento, el analista ve "hoy le toca pagar a X".
4. El inquilino paga (Yape o transferencia) y envía el voucher por WhatsApp.
5. El analista **sube el voucher**, lo asocia a inquilino, departamento y período, y registra el pago.
6. Una persona **verifica** el voucher (monto, período y que no esté repetido) → la cuota queda *Pagada*.
7. Si no hay pago: al día +N el sistema marca *Vencida*; al día +7 (configurable) **alerta al dueño** por correo o SMS.
8. El historial del inquilino se actualiza (puntualidad y atraso), y eso alimenta su **calificación**.

```
Cuota: Programada → Pendiente (vence hoy) → Pagada (por verificar) → Pagada (verificada)
                                   ↘ Vencida (atraso d días) → Alerta al dueño (d ≥ 7) → Pagada / Incobrable
```

## P-04. Programar incremento de alquiler
**AS-IS:** el dueño lo recuerda o lo anota.
**TO-BE**
1. Con unos **3 meses de anticipación**, el dueño entra al contrato y registra el **nuevo monto** con fecha de vigencia (por ejemplo, desde enero 2027: S/ 2 200).
2. El monto anterior **se conserva** en el historial (no se edita ni se borra).
3. Desde esa fecha, el sistema genera las cuotas con el nuevo monto.

## P-05. Prorrateo de servicios (agua y luz) – modalidad "el dueño paga"
**AS-IS:** el dueño toma la foto de cada submedidor, arma un Excel (lectura anterior, actual, consumo, factor y monto) y lo manda por WhatsApp con la copia del recibo.
**TO-BE**
1. El analista registra el **recibo** del proveedor (uno o más suministros) y sube el archivo.
2. Ingresa la **lectura actual** de cada submedidor, con **foto**; la lectura anterior se toma del mes previo.
3. El sistema calcula el **consumo** y el **monto por departamento** (ver 06).
4. Valida que **la suma de los montos sea igual al total del recibo** (ni pérdida ni ganancia).
5. Genera el **resumen** por inquilino (consumo, %, monto, más mantenimiento y limpieza) y lo **envía por correo**.
6. Las cuotas de servicios entran al mismo flujo de cobro que el P-03.
7. El dueño **paga** el recibo al proveedor y lo marca como pagado.

## P-06. Mantenimiento de áreas comunes y aprobación de gastos
1. El analista registra o solicita un gasto (vigilancia, limpieza, ascensor, reparaciones).
2. El dueño recibe un **mensaje** de "pendiente de aprobación" → aprueba o rechaza.
3. El gasto aprobado se refleja en la cuota de mantenimiento o en los egresos del inmueble.

## P-07. Rol de limpieza
1. El analista o el dueño genera el **cronograma** de limpieza por departamento (rangos de fechas).
2. Se notifica a cada inquilino su turno [INFERIDO: por correo].
3. El inquilino envía las fotos; el analista las sube y marca *Cumplido*, *Observado* o *Incumplido*.
4. Si el inquilino avisa que no puede o no cumple, se registra el **reemplazo** (persona contratada) y se genera un **cargo** al inquilino (por ejemplo, S/ 40).

## P-08. Registro de mejoras y valorización del inmueble
1. El dueño registra la mejora (fecha, descripción, monto y comprobantes).
2. El sistema suma la mejora al costo del inmueble.
3. Cada año, al registrar la **nueva UIT**, el sistema **recalcula automáticamente** el valor actualizado de todos los inmuebles.

## P-09. Cálculo de rendimiento del negocio inmobiliario
1. El sistema toma los ingresos cobrados (o esperados) y los impuestos y gastos del período.
2. Calcula el rendimiento mensual y anual por inmueble y por negocio, el **período de recuperación** y la comparación con la tasa de un plazo fijo de referencia.

## P-10. Cierre de mes (candado)
1. El dueño solicita cerrar el período (por ejemplo, octubre 2026).
2. El sistema verifica: **no hay deudas** del período, **todos los vouchers están subidos y verificados**, y todos los servicios y alquileres están **cancelados**.
3. Si todo está bien, el período queda **cerrado**: ya no se pueden modificar sus datos.
4. Si algo falla, muestra la lista de pendientes. [PREGUNTA P15: ¿se puede forzar el cierre con deudas pendientes, por ejemplo con un incobrable?]

## P-11. Salida y regreso de un inquilino
1. Al terminar el contrato se registra la salida, verificando que **no queden deudas** (alquiler y servicios).
2. El historial queda guardado.
3. Si el inquilino quiere regresar, se consulta su **récord** (fechas, atrasos, semáforo) para decidir.

## P-12. Gestión de inversiones financieras
1. El dueño registra o actualiza los saldos de cuentas, plazos fijos y operaciones de bolsa.
2. El sistema calcula el rendimiento % por instrumento y el total.
3. Se alerta del vencimiento de los plazos fijos.
4. A fin de año genera el **reporte de ganancias de capital** para el impuesto a la renta.

## P-13. Consulta del tablero y mensajes
1. Al entrar, el dueño ve una **tarjeta por negocio**: monto actual frente al objetivo del mes, en verde o rojo.
2. Hace clic en un negocio y entra a su módulo.
3. Ve los **mensajes** de los analistas; al abrirlos se marcan como leídos y desaparecen.

## P-14. Notificaciones automáticas a inquilinos
- Recordatorio de pago [INFERIDO], recibo de servicios, saludo de **cumpleaños**, aviso de renovación [INFERIDO].
