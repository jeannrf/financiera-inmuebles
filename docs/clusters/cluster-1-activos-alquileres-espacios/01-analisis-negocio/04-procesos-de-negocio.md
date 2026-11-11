# 04. Procesos de negocio

Reingeniería del estado manual (**AS-IS**) al flujo con la plataforma (**TO-BE**). Las secciones 4.1 y 4.2 son de la vertical piloto y
son también la base de las demás verticales. Los procesos del núcleo (alta de negocio, tablero, notificaciones) están en
[el documento general](../../../general/01-analisis-negocio/04-procesos-de-negocio.md).

## 4.1 Procesos de la vertical piloto

### C1-P-01. Alta de inmueble y departamentos
**AS-IS:** Anotaciones dispersas sobre medidores, costo de adquisición y suministros.
**TO-BE:**
1. El **Dueño** registra el inmueble: dirección, distrito, fecha base de adquisición/construcción, valor inicial de inversión y modalidad de servicios (*el dueño paga y prorratea* en zonas como San Martín de Porres vs. *inquilino paga directo / paquete todo incluido* en Jesús María).
2. Registra los suministros generales de agua y luz (soporta N suministros por edificio).
3. Crea las unidades/departamentos: código libre (ej. "1A", "2B", "501"), piso y submedidores vinculados con sus identificadores.
4. El sistema fija el costo base del activo para procesar las valorizaciones automáticas por indexación a la UIT y acumulado de mejoras (Capex).

### C1-P-02. Alta de inquilino y formalización de contrato
**AS-IS:** Documentos en papel, contactos informales en WhatsApp y falta de expediente estructurado para contingencias legales.
**TO-BE:**
1. El **Analista** o **Dueño** busca al inquilino por DNI en la base centralizada para verificar su historial y calificación previa (semáforo de morosidad).
2. Carga el expediente digital: DNI escaneado, datos laborales (razón social de la empresa, RUC, dirección del centro de trabajo) y **boleta de pago**. *Propósito:* blindar la notificación legal en el centro laboral ante un eventual juicio de desalojo.
3. El **Dueño** define el contrato: asigna el departamento, período de vigencia, día de pago mensual, monto de alquiler y conceptos asociados.
4. El motor de cobros del Core genera el plan proyectado de obligaciones mensuales y programa las alertas de vencimiento de contrato.

### C1-P-03. Flujo central de cobro mensual y fiscalización operativa
**AS-IS:** El dueño revisa manualmente vouchers en WhatsApp contra Excel, persigue inquilinos y sufre falta de reporte oportuno por parte de los analistas.
**TO-BE:**
1. **El sistema (proceso automático):** Genera la cuota mensual del departamento con el monto vigente para el período.
2. El **Analista** consulta su vista operativa (con montos agrupados restringidos según RBAC) para identificar los cobros de la semana.
3. El inquilino envía el voucher de pago (Yape, Plin, transferencia o efectivo). El **Analista** sube el archivo al sistema asociándolo de forma estricta: `Inquilino + Departamento + Período (ej. Abril 2026)`.
4. **Verificación humana asistida:** El analista/dueño valida que la referencia, monto y período coincidan, descartando vouchers duplicados, consumidos o de otros meses/departamentos. Al confirmar, la cuota cambia a *Pagada*.
5. **Control de morosidad y fiscalización del analista:**
   * Si no hay pago al vencimiento, la cuota pasa a *Vencida*.
   * Al alcanzar **+N días de atraso (ej. 5 a 7 días)**, el sistema dispara una **Alerta Crítica al Dueño** (SMS/Correo). Esto le notifica la deuda y fiscaliza si el analista omitió reportar la morosidad.
6. El historial actualiza automáticamente la **Calificación (Semáforo Verde, Amarillo o Rojo)** del inquilino.

```
Flujo del Estado de la Cuota:
[Programada] ➔ [Pendiente (Vence hoy)] ➔ [Pagada (Por verificar)] ➔ [Pagada (Verificada)]
                                       ↘ [Vencida (días de atraso)] ➔ [ALERTA AL DUEÑO (d ≥ N)] ➔ [Cobrado / Dossier Desalojo]
```

### C1-P-04. Incrementos programados de alquiler
**AS-IS:** Dependencia de la memoria del dueño o anotaciones manuales para aplicar aumentos de renta.
**TO-BE:**
1. Con **3 meses de anticipación**, el **Dueño** registra en el contrato la tarifa ajustada y su fecha futura de entrada en vigencia.
2. El Core preserva el historial de tarifas previas como registros inmutables (no se editan ni se eliminan).
3. Al llegar la fecha, el motor de cuotas emite automáticamente los cobros ajustados.

### C1-P-05. Prorrateo de servicios (Agua y Luz) – Modalidad "El dueño paga"
**AS-IS:** El dueño toma fotos de submedidores, calcula prorrateos en Excel y envía cobros por WhatsApp, con riesgo de asumir deudas de inquilinos que se retiran.
**TO-BE:**
1. El **Analista** registra el recibo del proveedor (Sedapal, Enel, Luz del Sur), sube la factura digital e ingresa el monto y consumo global del edificio.
2. Registra la **lectura actual** del submedidor de cada departamento adjuntando **evidencia fotográfica** (el sistema recupera automáticamente la lectura del mes anterior).
3. El sistema calcula el consumo individual, aplica la fórmula de prorrateo y valida que la suma de cobros sea exactamente igual al 100% del recibo del proveedor.
4. Anexa los conceptos de agua, luz y mantenimiento al estado de cuenta del inquilino (unificado con el proceso C1-P-03) y emite un desglose en PDF por correo.

### C1-P-06. Mantenimiento común y flujo de aprobación de egresos
**AS-IS:** Gastos operativos ejecutados sin control previo de caja ni aprobación centralizada.
**TO-BE:**
1. El **Analista** registra una solicitud de gasto para el edificio (servicios de vigilancia, mantenimiento de ascensor, limpieza o reparaciones).
2. El sistema envía una notificación de "Aprobación Pendiente" al panel del **Dueño**.
3. El **Dueño** autoriza o rechaza el gasto.
4. Si se aprueba, el monto se distribuye en la cuota de mantenimiento de los ocupantes o se registra en los egresos directos del inmueble.

### C1-P-07. Gestión del rol de limpieza de áreas comunes
**AS-IS:** Descontrol en el turno rotativo de limpieza de pasadizos y escaleras por departamento.
**TO-BE:**
1. El sistema genera el cronograma de turnos de limpieza asignado a cada departamento.
2. El inquilino sube fotos de evidencia al cumplir su turno.
3. El **Analista** verifica las imágenes en el sistema y actualiza el estado: *Programado ➔ Reportado ➔ Cumplido*.
4. En caso de incumplimiento o solicitud de reemplazo, el analista registra la contratación del servicio sustituto y el sistema carga automáticamente la multa/recargo (ej. S/ 40) en la cuota del inquilino.

### C1-P-08. Valorización del activo (UIT + Mejoras / Capex)
**AS-IS:** Imposibilidad de visualizar la revalorización contable y comercial de las propiedades.
**TO-BE:**
1. El **Dueño** registra los egresos por mejoras de capital (Capex) efectuados sobre el inmueble (ej. renovación de pisos por S/ 50,000) respaldados por comprobantes.
2. El sistema suma las mejoras al valor contable acumulado de la propiedad.
3. Al registrar la **nueva UIT** anual en la parametrización central del sistema, el módulo indexa y recalcula automáticamente el valor actualizado de todos los inmuebles.

### C1-P-09. Análisis de rentabilidad inmobiliaria (ROI / Cap Rate)
**AS-IS:** Incertidumbre sobre el retorno real de los activos inmobiliarios frente a opciones financieras de menor riesgo.
**TO-BE:**
1. El sistema consolida los ingresos netos percibidos por alquileres (deduciendo impuestos, mantenimiento y vacancia).
2. Calcula automáticamente el rendimiento mensual y anualizado (**Cap Rate / ROI**) sobre el valor actualizado del inmueble.
3. Presenta una comparativa en tiempo real frente a la tasa promedio ponderada de los depósitos a plazo fijo registrados en el módulo financiero.

### C1-P-10. Cierre de mes (Candado de auditoría)
**AS-IS:** Alteración de registros pasados en hojas de cálculo sin rastro de auditoría.
**TO-BE:**
1. Al finalizar el período, el **Dueño** solicita ejecutar el **Cierre de Mes**.
2. El sistema valida las precondiciones: ausencia de cobros pendientes de verificación, servicios totalmente prorrateados y conciliación completa de cuotas (*Pagadas* o declaradas como *Incobrables*).
3. Al confirmarse, el sistema aplica un **candado digital**: se bloquea cualquier edición o eliminación retroactiva de datos en ese período.

### C1-P-11. Salida y reingreso de inquilinos
**AS-IS:** Pérdida de antecedentes y datos de morosidad cuando un inquilino vuelve a alquilar un departamento años después.
**TO-BE:**
1. Se procesa la liquidación de salida constatando que no existan deudas pendientes de alquiler ni de servicios prorrateados.
2. El contrato pasa a estado *Finalizado*, conservando el expediente del inquilino en la base de datos centralizada.
3. Si el inquilino solicita un nuevo alquiler, el sistema recupera su expediente histórico y su semáforo de cumplimiento para respaldar la aprobación del nuevo contrato.

## 4.2 Puntos por conciliar

Esta versión de los procesos reemplaza a la anterior. Al compararlas aparecen diferencias que hay que resolver:

| Proceso | Diferencia | Qué falta decidir |
|---------|------------|-------------------|
| C1-P-05 | La versión anterior terminaba con "el dueño paga el recibo y lo marca como pagado" (C1-RF-41). Ya no aparece | ¿Se mantiene? Sin este paso no se controla la deuda con el proveedor |
| C1-P-07 | Ahora "el inquilino sube las fotos", pero el inquilino no usa el sistema en las etapas 1-2 ([C1-Q-30](08-preguntas-abiertas.md)) | Portal del inquilino en etapa 3, o que el analista las suba hasta entonces |
| C1-P-07 | Antes había estados *Observado*, *Incumplido* y *Reemplazado*; ahora solo *Programado → Reportado → Cumplido*, aunque el paso 4 trata el incumplimiento | Conservar los estados completos en el modelado |
| C1-P-09 | Ahora se calcula sobre el **valor actualizado** y descuenta la **vacancia**. Antes se proponía mostrar ambas bases, y la vacancia no tenía fórmula | **Actualizado con P11 (11/Nov/2026):** el cliente usa el **rendimiento por m²** con precios de mercado y depreciación ([B1-bis](05-reglas-de-negocio-y-calculos.md#b1-bis-rendimiento-de-mercado-por-metro-cuadrado-método-del-piloto)). El paso 2 debe decir "sobre el valor de mercado por m² depreciado", y hay que añadir un paso previo: el analista registra el estudio de mercado. Falta definir la vacancia (C1-Q-40) |
| C1-P-09 | Ya no menciona el período de recuperación ni el alquiler requerido, que el cliente sí usó en la reunión | Se conservan en la regla B1 |
| C1-P-09 | Compara contra la tasa del módulo financiero, pero un negocio puede no tenerlo | Si el módulo no está activo, se usa una tasa de referencia manual |
| C1-P-10 | Admite cuotas *Incobrables*. Esto responde parte de [C1-Q-15](08-preguntas-abiertas.md); falta saber quién las declara y si se puede reabrir | **Actualizado con P12:** la deuda pasa a incobrable a los **7 días** si no hubo pedido de pago por partes, y se **suspenden agua y luz** (C1-RN-45, C1-RN-46). Esto vuelve más frecuente el incobrable y facilita el cierre. Falta quién confirma (C1-Q-68) y si se puede reabrir un mes (C1-Q-15) |
| C1-P-03 / C1-P-10 | P12 agrega un flujo que no estaba: **suspensión y reposición de servicios** | Modelarlo como subproceso de la cobranza: día 7 → propuesta → confirmación del dueño → orden al analista → registro de la suspensión → reposición al pagar |
| C1-P-03 | "Dossier Desalojo" aparece en el flujo sin definición | Ver [C1-Q-39](08-preguntas-abiertas.md) |
| C1-P-02 | La "base centralizada" de inquilinos se limita a la organización | Ver [NUC-Q-06](../../../general/01-analisis-negocio/08-preguntas-abiertas.md) |

## 4.3 Procesos de las demás verticales [INFERIDO a partir del mapeo]

Reutilizan C1-P-02, C1-P-03 y C1-P-04 (contrato, cobro e incrementos). Solo se describe lo que agregan.

### C1-P-20. Comercialización de unidades (1.1)
Visita agendada → Oferta o reserva → Evaluación crediticia → Firma de contrato. Al firmar, la unidad pasa a *Alquilado* y se ejecuta C1-P-02.

### C1-P-21. Liquidación a propietarios (1.1)
1. Al cierre, el sistema toma los cobros de las unidades de cada propietario.
2. Resta la comisión de administración y las reparaciones autorizadas.
3. Genera el estado de liquidación y la obligación de transferir el saldo. El dueño la aprueba y registra el pago.

### C1-P-22. Emisión masiva de recibos del edificio (1.2)
1. Se registran los gastos del mes, las lecturas y el aporte al fondo de reserva.
2. El sistema reparte por consumo o por alícuota, y emite todos los recibos con cuadre exacto.
3. Publica el estado de cuenta por residente y el reporte de morosidad.

### C1-P-23. Reserva de áreas comunes (1.2)
El residente o la administración reserva el SUM, la parrilla o la sala; el sistema evita choques y, si corresponde, genera un cargo.

### C1-P-24. Entrega y devolución de un bien (1.3)
1. **Reserva:** se comprueba disponibilidad, tarifa y documentos; se bloquea la garantía.
2. **Check-out:** acta digital con fotos, kilometraje u horómetro, combustible y accesorios.
3. **Check-in:** nueva acta; el sistema compara y calcula exceso de km, combustible, daños y multas.
4. Se liquida contra la garantía. La unidad pasa a *En patio* o *En taller*.

### C1-P-25. Mantenimiento preventivo de la flota (1.3)
Alertas por kilometraje, horómetro, seguros y revisiones técnicas. Si la unidad está *En taller*, no se puede alquilar; el costo va a su centro de costo.

### C1-P-26. Membresías y créditos (1.4)
1. Se vende una membresía con espacio y créditos mensuales.
2. El día 1 se factura y se renuevan los créditos.
3. Cada reserva de sala o impresión consume créditos; el exceso se cobra como adicional.
