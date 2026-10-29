# 06. Reglas de negocio y cálculos

> Las fórmulas son una **propuesta** basada en lo que explicó el cliente. Todos los números son
> ilustrativos. Los temas tributarios **deben validarse con un contador** antes de implementarlos.

---

## A. Reglas generales

| ID | Regla | Origen |
|----|-------|--------|
| RN-01 | **Nada se borra:** los montos de alquiler, pagos y vouchers históricos no se eliminan ni se sobrescriben. Un cambio de monto crea un **nuevo registro con fecha de vigencia**. | [CONFIRMADO] "No es editar, sino colocarlo nuevo" |
| RN-02 | El monto de una cuota es el **monto vigente** del contrato en ese período (el último registro con `fecha_vigencia ≤ inicio del período`). | [INFERIDO de RN-01] |
| RN-03 | Los incrementos se pueden programar con antelación (unos 3 meses, hasta 1 año). | [CONFIRMADO] |
| RN-04 | El sistema **no interpreta** los vouchers; **una persona** los verifica. | [CONFIRMADO] |
| RN-05 | Cada voucher se asocia a **inquilino + departamento + período + concepto**. | [CONFIRMADO] "este voucher corresponde a enero 2026" |
| RN-06 | Un pago con atraso de **≥ 7 días** (valor configurable) genera una alerta al **dueño** por correo o SMS. | [CONFIRMADO; el cliente dijo 5 y 7 días → P13] |
| RN-07 | El analista recibe **cada semana** la lista de cobros de la semana. | [CONFIRMADO] |
| RN-08 | Una **mejora siempre se suma** al costo o valor del inmueble. | [CONFIRMADO] |
| RN-09 | El valor del inmueble se actualiza automáticamente con la **UIT** cada año. | [CONFIRMADO] |
| RN-10 | En el prorrateo de servicios **no puede haber pérdida ni ganancia**: la suma cobrada a los departamentos es igual al total del recibo. | [CONFIRMADO] |
| RN-11 | Un período **cerrado** no admite cambios. Solo se cierra si no hay deudas, faltan vouchers ni servicios por cancelar. | [CONFIRMADO] |
| RN-12 | El analista **no ve** ganancias, rendimientos, valorizaciones ni totales de dinero. | [CONFIRMADO] |
| RN-13 | Los analistas pueden ser N; cada usuario tiene un cargo o rol. | [CONFIRMADO] |
| RN-14 | Si un inquilino no cumple su turno de limpieza, se contrata un reemplazo y **se le cobra** el costo. | [CONFIRMADO] |
| RN-15 | Los gastos de mantenimiento que registra el analista requieren **aprobación del dueño**. | [CONFIRMADO, por el ejemplo del mensaje] |
| RN-16 | No hay descuentos por pronto pago ni por cumpleaños. | [CONFIRMADO] "No hay descuento" |
| RN-17 | En el negocio financiero, el impuesto se calcula **solo sobre las ganancias**; si hay pérdida, no se paga. | [CONFIRMADO] |
| RN-18 | El sistema debe soportar **N negocios**, cada uno con su objetivo mensual. | [CONFIRMADO] |

---

## B. Cálculos del negocio inmobiliario

### B1. Ingreso anual y rendimiento de un inmueble

```
Ingreso bruto anual   = alquiler mensual × 12
Ingreso neto anual    = ingreso bruto anual − impuestos (renta + predial + arbitrios) − gastos no trasladados [P16]
Rendimiento anual %   = ingreso neto anual / inversión total × 100
Rendimiento mensual % = (ingreso neto anual / 12) / inversión total × 100
Años de recuperación  = inversión total / ingreso neto anual
Inversión total       = costo de adquisición o construcción + Σ mejoras
```

**Ejemplo de la reunión:**

| Concepto | Valor |
|----------|-------|
| Inversión | S/ 500 000 |
| Alquiler | S/ 2 500 × 12 = **S/ 30 000** al año |
| Impuestos (supuesto) | S/ 2 000 |
| Ingreso neto | **S/ 28 000** |
| Rendimiento anual | 28 000 / 500 000 = **5.6 %** |
| Rendimiento mensual | 2 333.33 / 500 000 = **0.47 %** |
| Recuperación | 500 000 / 28 000 = **17.9 años** |

**Interpretación del cliente:** lo sano es recuperar la inversión en **12–15 años**, es decir, un
rendimiento neto de **6.7 % – 8.3 %**. Con 5.6 % el inmueble **rinde menos que un plazo fijo**
(5.7–5.8 % en comparabien.com, "sin hacer nada"). La corrección es **subir el alquiler** (si el mercado
lo permite) o **bajar el costo** de la siguiente compra (comprar en planos o construir: unos S/ 300 000).

→ El sistema debe mostrar esta comparación: **rendimiento del inmueble frente a la tasa de referencia
de un plazo fijo** (tasa configurable por el dueño) y el **alquiler necesario** para lograr la meta de años:

```
Alquiler mensual requerido = (inversión / años_meta + impuestos anuales) / 12
Ej.: (500 000 / 15 + 2 000) / 12 = S/ 2 944.44
```

[PREGUNTA P16: ¿el rendimiento se calcula sobre la **inversión** (costo + mejoras) o sobre el **valor
actualizado** por UIT? Proponemos mostrar ambos: "rendimiento sobre inversión" y "rendimiento sobre
valor actual".]

[PREGUNTA P17: ¿los ingresos se consideran **cobrados** (caja) o **devengados** (lo que se debía cobrar)?
Proponemos usar los cobrados para el rendimiento real y los devengados para el proyectado.]

> **Referencia tributaria (validar con contador):** en Perú, la renta de primera categoría (alquileres)
> de una persona natural tributa un **5 % efectivo sobre la renta bruta** (6.25 % sobre el 80 %). Sobre
> S/ 30 000 serían unos S/ 1 500. El impuesto predial y los arbitrios dependen de la municipalidad.
> En el sistema conviene que los impuestos sean **montos o tasas configurables**, no fijos en el código.

### B2. Valorización del inmueble ligada a la UIT

El cliente quiere que el valor "suba solito" con la UIT, sin tener que estimarlo.

```
Factor UIT(año) = UIT(año actual) / UIT(año base)
Valor actualizado = valor base × Factor UIT  +  Σ (mejora_k × UIT(año actual) / UIT(año de la mejora_k))   [P18]
```

**Ejemplo del cliente:** un inmueble valorado cuando la UIT era S/ 2 800, hoy con UIT de S/ 5 300:

```
Factor = 5 300 / 2 800 = 1.8929
Valor  = 500 000 × 1.8929 = S/ 946 428.57
```

- Se necesita una **tabla de UIT por año**, que el dueño actualiza una vez al año (la UIT se publica por
  decreto supremo cada diciembre). Referencia: UIT 2025 = S/ 5 350; el valor de 2026 está por confirmar al cargarlo.
- [PREGUNTA P18: ¿las mejoras también se indexan con la UIT desde su año, o se suman a su valor nominal?]
- Nota conceptual: indexar a la UIT es una **aproximación** elegida por el cliente (no es una tasación).
  Conviene permitir también un **valor de tasación manual** opcional.

### B3. Prorrateo de servicios (agua y luz)

**Consumo de cada departamento:**
```
consumo_i = lectura_actual_i − lectura_anterior_i
```
Ejemplo del cliente: lectura actual 57, lectura anterior 45 → **12 m³**.

Hay **dos métodos** posibles; el cliente usó ambos según el ejemplo. Hay que confirmar cuál (P19).

**Método A, proporcional (garantiza RN-10):**
```
monto_i = total_recibo × consumo_i / Σ consumo_j
```

| Dpto | Ant. | Act. | Consumo | % | Monto (recibo S/ 300) |
|------|-----:|-----:|--------:|--:|------:|
| 1A | 45 | 57 | 12 | 20 % | S/ 60.00 |
| 1B | 30 | 48 | 18 | 30 % | S/ 90.00 |
| 2A | 70 | 100 | 30 | 50 % | S/ 150.00 |
| **Total** | | | **60** | **100 %** | **S/ 300.00** |

**Método B, tarifa o factor unitario** (el cliente mencionó "un factor de 0.87"):
```
factor  = total_recibo / consumo total facturado      (S/ por kWh o por m³)
monto_i = consumo_i × factor
```
Con este método, si la suma de los submedidores **no coincide** con el medidor general (áreas comunes,
pérdidas), queda una **diferencia** que hay que repartir para que no haya pérdida:
- en partes iguales entre los departamentos, o
- proporcional al consumo, o
- como cargo de "áreas comunes" dentro del mantenimiento. [PREGUNTA P19]

**Varios suministros:** si el edificio tiene 2 recibos de luz, `total_recibo = Σ recibos`.

**Redondeo:** se redondea a 2 decimales y el residuo de céntimos se asigna al departamento de mayor consumo,
para que la suma sea exacta. [INFERIDO]

**Resumen por inquilino (lo que se envía por correo):**

| Concepto | Monto |
|----------|------:|
| Agua (consumo X m³, Y %) | S/ … |
| Luz (consumo X kWh, Y %) | S/ … |
| Mantenimiento | S/ … |
| Limpieza (si aplica) | S/ … |
| **Total servicios** | **S/ …** |

Con adjuntos: la copia de los recibos del proveedor y las fotos de su medidor.

### B4. Días de atraso y estado de la cuota

```
dias_atraso = max(0, hoy − fecha_vencimiento)   si la cuota no está pagada
estado      = PAGADA        si hay un pago verificado ≥ monto
              PENDIENTE     si hoy ≤ fecha_vencimiento
              VENCIDA       si 0 < dias_atraso < umbral_alerta
              MOROSA        si dias_atraso ≥ umbral_alerta (7) → alerta al dueño
```
[PREGUNTA P24: ¿se aceptan **pagos parciales**? ¿Hay **mora o penalidad** por atraso?]

### B5. Calificación del inquilino (semáforo)

Inspirada en las centrales de riesgo (Sentinel / Infocorp), con **criterios ponderados**. El cliente dijo
que los criterios son **solo de pagos**. Propuesta configurable:

| Criterio | Cálculo | Peso propuesto |
|----------|---------|---------------:|
| Puntualidad | % de cuotas pagadas a tiempo | 50 % |
| Atraso promedio | 100 − (días promedio de atraso × factor) | 30 % |
| Deuda vigente | 100 si no tiene deuda; menos según el monto | 20 % |

```
puntaje = Σ (peso_k × puntaje_k)   (0 a 100)
Verde ≥ 80   ·   Amarillo 50–79   ·   Rojo < 50
```
También cuenta el historial de contratos anteriores (si el inquilino regresa). [PREGUNTA P25: validar los criterios y los pesos]

### B6. Tablero: estado del negocio frente al objetivo

```
avance % = monto real del mes / objetivo del mes × 100
Verde si avance ≥ 100 % (o ≥ lo esperado a la fecha)   ·   Rojo si está por debajo
```
Ejemplo del cliente: objetivo 120 al mes de octubre; real 116 → rojo; real 160 → verde.
Rojo también significa que "alguien no ha pagado" → al hacer clic se ven las cuentas pendientes.
[PREGUNTA P26: ¿qué representa exactamente el "monto" de la tarjeta: ingresos del mes, acumulado del año o patrimonio?]

---

## C. Cálculos del negocio financiero

### C1. Cuenta bancaria
```
Interés anual estimado = saldo × TEA
Rendimiento %          = TEA
Plazo                  = indefinido
```

### C2. Depósito a plazo fijo (convención de 360 días, usada por la banca peruana)
```
Interés = monto × ((1 + TEA)^(días / 360) − 1)
```
Ejemplo: S/ 100 000 al 7 % TEA por 180 días → 100 000 × (1.07^0.5 − 1) = **S/ 3 440.80**.
Alerta X días antes de la fecha de vencimiento.

### C3. Operación bursátil (trading)

```
Costo real de compra  = cantidad × precio_bolsa_compra + comisión bróker + costos BVL/CAVALI/SMV + IGV
Ingreso neto de venta = cantidad × precio_bolsa_venta − comisión bróker − costos BVL/CAVALI/SMV − IGV
Ganancia o pérdida    = ingreso neto de venta − costo real de compra
Rendimiento %         = ganancia / costo real de compra × 100
```

**Ejemplo con las cifras de la reunión** (1 000 acciones):

| | Precio bolsa | Precio real (con costos) | Monto |
|---|---:|---:|---:|
| Compra | 3.74 | 3.84 | S/ 3 840 |
| Venta | 4.05 | 3.95 *(supuesto)* | S/ 3 950 |
| **Ganancia** | | | **S/ 110 → 2.86 %** |

> ⚠ En la reunión se dijo "venta real 4.06", que es mayor que el precio de bolsa (4.05). En una venta los
> costos **se restan**, así que el neto debería ser menor. Hay que confirmarlo con el cliente (P27).
> Tampoco quedó claro si el bróker cobra **2 %** o **0.2 %** (P27).

### C4. Rendimiento de una acción incluyendo utilidades o dividendos (preferencia del cliente)
```
Rendimiento total % = (ganancias realizadas + dividendos/utilidades recibidos + ganancia no realizada [P23]) / inversión total × 100
```
El cliente quiere comparar el % de cada acción (por ejemplo, 3 %, 7 %, 17 %) para decidir de cuál salir.

### C5. Resumen y rendimiento ponderado de la cartera
```
Total invertido = Σ cuentas + Σ plazos fijos + Σ bolsa
Rendimiento ponderado % = Σ (monto_k × rendimiento_k) / total invertido
```

### C6. Reporte tributario anual (ganancias de capital)
```
Ganancia neta del año = Σ ganancias − Σ pérdidas   (operaciones realizadas en el año)
Impuesto estimado     = max(0, ganancia neta − exoneración aplicable) × 5 %
```
> **Validar con contador:** para personas naturales domiciliadas, la ganancia de capital por venta de
> valores tributa un **5 % efectivo**. Existe o ha existido una **exoneración de las primeras 5 UIT** para
> valores negociados en la BVL bajo ciertas condiciones. El sistema solo debe **calcular y reportar**;
> la tasa y la exoneración deben ser **parámetros configurables**.
