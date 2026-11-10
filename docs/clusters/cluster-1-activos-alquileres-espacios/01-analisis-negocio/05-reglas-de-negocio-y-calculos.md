# 05. Reglas de negocio y cálculos

> Las fórmulas son una **propuesta** basada en lo que explicó el cliente piloto. Todos los números son
> ilustrativos. Los temas tributarios **deben validarse con un contador** antes de implementarlos.
> Las reglas universales (`NUC-RN`) están en [el documento general](../../../general/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md).

---

## A. Reglas de la vertical piloto

| ID | Regla | Origen |
|----|-------|--------|
| C1-RN-03 | Los incrementos se pueden programar con antelación (unos 3 meses, hasta 1 año). | [CONFIRMADO] |
| C1-RN-05 | Cada voucher se asocia a **inquilino + departamento + período + concepto**. | [CONFIRMADO] "este voucher corresponde a enero 2026" |
| C1-RN-06 | Un pago con atraso de **≥ 7 días** (valor configurable) genera una alerta al **dueño** por **correo electrónico y bandeja del sistema**. | [CONFIRMADO — cuestionario P7, 10/Nov/2026; cierra C1-Q-13] |
| C1-RN-07 | El analista recibe **cada semana** la lista de cobros de la semana. | [CONFIRMADO] |
| C1-RN-08 | Una **mejora siempre se suma** al costo o valor del inmueble. | [CONFIRMADO] |
| C1-RN-09 | El valor del inmueble se actualiza automáticamente con la **UIT** cada año. | [CONFIRMADO] |
| C1-RN-10 | En el prorrateo de servicios **no puede haber pérdida ni ganancia**: la suma cobrada a los departamentos es igual al total del recibo. | [CONFIRMADO] |
| C1-RN-14 | Si un inquilino no cumple su turno de limpieza, se contrata un reemplazo y **se le cobra** el costo. | [CONFIRMADO] |
| C1-RN-16 | No hay descuentos por pronto pago ni por cumpleaños. | [CONFIRMADO] "No hay descuento" |
| C1-RN-19 | Un inquilino con deudas no puede finalizar su contrato sin liquidación. | [Proceso C1-P-11] |
| C1-RN-39 | Se aceptan **pagos parciales**: una cuota puede recibir varios pagos, cada uno con su voucher, y queda en *Pago parcial* con su **saldo pendiente** hasta completarse. | [CONFIRMADO — P8] |
| C1-RN-40 | El piloto **no cobra intereses ni penalidad** por mora: solo se exige el saldo pendiente. | [CONFIRMADO — P8] |
| C1-RN-41 | El prorrateo de servicios es **proporcional al consumo** de cada departamento y se hace **por suministro**: cada recibo se reparte solo entre los departamentos conectados a ese suministro. | [CONFIRMADO — P10; cierra C1-Q-19] |
| C1-RN-42 | La meta del negocio de alquiler es la **ocupación total**: una unidad libre es una alerta para el dueño, aunque la cobranza del mes esté al día. | [CONFIRMADO — P6] |

## A2. Reglas de las demás verticales [INFERIDO a partir del mapeo]

| ID | Regla | Vertical |
|----|-------|----------|
| C1-RN-30 | Una unidad no puede tener dos contratos ni reservas que se traslapen. | Todas |
| C1-RN-31 | La **garantía no es ingreso**: se registra como dinero de terceros hasta que se aplica o se devuelve. | Todas |
| C1-RN-32 | Una unidad *En taller* o *En mantenimiento* no se puede alquilar. | 1.1, 1.3 |
| C1-RN-33 | Los gastos comunes se reparten por consumo o por alícuota, y la suma cuadra con el total. | 1.2 |
| C1-RN-34 | El fondo de reserva se lleva separado de los gastos del mes. | 1.2 |
| C1-RN-35 | Toda entrega y devolución requiere un acta con evidencia. | 1.3 |
| C1-RN-36 | Los créditos no usados se pierden o se acumulan según el plan. | 1.4 |
| C1-RN-37 | Una penalidad por mora o el ajuste por IPC son **parámetros por vertical**: el mapeo los incluye en 1.1, mientras que el piloto **no cobra mora** (C1-RN-40) y usa incrementos manuales. | 1.1 |
| C1-RN-38 | La alerta de morosidad escala: analista (N₁ días) → dueño (N₂ días). N₁ y N₂ son parámetros. El dueño recibe el nivel 2 aunque el analista no haya hecho nada. | [CONFIRMADO — PPT cliente; N₂ = 7 días, P7] + [PREGUNTA C1-Q-56: N₁] |

---

## B. Cálculos

### B1. Ingreso anual y rendimiento de un inmueble

```
Ingreso bruto anual   = alquiler mensual × 12
Ingreso neto anual    = ingreso bruto anual − impuestos (renta + predial + arbitrios) − gastos no trasladados [C1-Q-16]
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

[PREGUNTA C1-Q-16: ¿el rendimiento se calcula sobre la **inversión** (costo + mejoras) o sobre el **valor
actualizado** por UIT? Proponemos mostrar ambos: "rendimiento sobre inversión" y "rendimiento sobre
valor actual".]

[PREGUNTA C1-Q-17: ¿los ingresos se consideran **cobrados** (caja) o **devengados** (lo que se debía cobrar)?
Proponemos usar los cobrados para el rendimiento real y los devengados para el proyectado.]

> **Referencia tributaria (validar con contador):** en Perú, la renta de primera categoría (alquileres)
> de una persona natural tributa un **5 % efectivo sobre la renta bruta** (6.25 % sobre el 80 %). Sobre
> S/ 30 000 serían unos S/ 1 500. El impuesto predial y los arbitrios dependen de la municipalidad.
> En el sistema conviene que los impuestos sean **montos o tasas configurables**, no fijos en el código.

### B2. Valorización del inmueble ligada a la UIT

El cliente quiere que el valor "suba solito" con la UIT, sin tener que estimarlo.

```
Factor UIT(año) = UIT(año actual) / UIT(año base)
Valor actualizado = valor base × Factor UIT  +  Σ (mejora_k × UIT(año actual) / UIT(año de la mejora_k))   [C1-Q-18]
```

**Ejemplo del cliente:** un inmueble valorado cuando la UIT era S/ 2 800, hoy con UIT de S/ 5 300:

```
Factor = 5 300 / 2 800 = 1.8929
Valor  = 500 000 × 1.8929 = S/ 946 428.57
```

- Se necesita una **tabla de UIT por año**, que el dueño actualiza una vez al año (la UIT se publica por
  decreto supremo cada diciembre). Referencia: UIT 2025 = S/ 5 350; el valor de 2026 está por confirmar al cargarlo.
- [PREGUNTA C1-Q-18: ¿las mejoras también se indexan con la UIT desde su año, o se suman a su valor nominal?]
- Nota conceptual: indexar a la UIT es una **aproximación** elegida por el cliente (no es una tasación).
  Conviene permitir también un **valor de tasación manual** opcional.

### B3. Prorrateo de servicios (agua y luz)

**Consumo de cada departamento:**
```
consumo_i = lectura_actual_i − lectura_anterior_i
```
Ejemplo del cliente: lectura actual 57, lectura anterior 45 → **12 m³**.

> **Respuesta del cliente (P10, 10/Nov/2026)** [CONFIRMADO]: cada departamento tiene **medidor de agua y de luz**. El consumo es
> la lectura actual menos la del mes pasado. La **suma de los consumos** de los departamentos es el consumo total. El proveedor
> manda el monto total (**agua y alcantarillado**, y **luz**), y a cada departamento se le asigna un monto **proporcional a su
> consumo**. Unos departamentos pueden tener un **suministro de luz distinto** al de otros. → Se adopta el **método A, por suministro**.

**Método A, proporcional — método del piloto (garantiza C1-RN-10 y C1-RN-41):**
```
monto_i = total_recibo × consumo_i / Σ consumo_j
```

| Dpto | Ant. | Act. | Consumo | % | Monto (recibo S/ 300) |
|------|-----:|-----:|--------:|--:|------:|
| 1A | 45 | 57 | 12 | 20 % | S/ 60.00 |
| 1B | 30 | 48 | 18 | 30 % | S/ 90.00 |
| 2A | 70 | 100 | 30 | 50 % | S/ 150.00 |
| **Total** | | | **60** | **100 %** | **S/ 300.00** |

Como el método reparte el **monto total del recibo** según el porcentaje de consumo, cualquier consumo de áreas comunes o
pérdida queda absorbido de forma proporcional: **no hay diferencia que repartir** y la suma cobrada es igual al recibo.
El "factor 0.87" del Excel del cliente es solo el resultado intermedio `total_recibo / Σ consumo_j` (S/ por unidad), que
multiplicado por cada consumo da el mismo monto que el porcentaje.

**Método B, tarifa o factor unitario sobre el medidor general** (no lo usa el piloto; queda como alternativa configurable para otros clientes):
```
factor  = total_recibo / consumo total facturado      (S/ por kWh o por m³)
monto_i = consumo_i × factor
```
Con este método, si la suma de los submedidores **no coincide** con el medidor general (áreas comunes,
pérdidas), queda una **diferencia** que hay que repartir para que no haya pérdida:
- en partes iguales entre los departamentos, o
- proporcional al consumo, o
- como cargo de "áreas comunes" dentro del mantenimiento.

**Varios suministros** [CONFIRMADO — P10]: el prorrateo se hace **por suministro**. Cada recibo se reparte solo entre los
departamentos conectados a ese suministro:

```
Para cada suministro s:
    monto_i,s = total_recibo_s × consumo_i / Σ consumo_j   (j = departamentos del suministro s)
```

Ejemplo: si los departamentos 1A, 1B y 2A están en el suministro de luz L1 y 2B y 3B en L2, el recibo de L1 se reparte entre
1A, 1B y 2A, y el de L2 entre 2B y 3B. El agua puede tener un solo suministro para todos. ~~Si el edificio tiene 2 recibos de luz,
`total_recibo = Σ recibos`~~ (reemplazado: sumar los recibos solo vale si todos los departamentos comparten ambos suministros).

**Agua y alcantarillado:** el recibo de Sedapal trae ambos conceptos; se reparten juntos según el consumo de agua [INFERIDO → C1-Q-61].

**Redondeo:** se redondea a 2 decimales y el residuo de céntimos se asigna al departamento de mayor consumo,
para que la suma sea exacta. [INFERIDO]

**Resumen por inquilino (lo que se envía por correo):**

| Concepto | Monto |
|----------|------:|
| Agua y alcantarillado (consumo X m³, Y %) | S/ … |
| Luz (consumo X kWh, Y %) | S/ … |
| Mantenimiento | S/ … |
| Limpieza (si aplica) | S/ … |
| **Total servicios** | **S/ …** |

Con adjuntos: la copia de los recibos del proveedor y las fotos de su medidor.

### B4. Días de atraso y estado de la cuota

Respuesta del cliente (P8) [CONFIRMADO]: **sí** hay pagos parciales y **no** se cobra interés ni penalidad.

```
pagado      = Σ pagos verificados de la cuota
saldo       = monto − pagado                       (sin intereses ni penalidad: C1-RN-40)
dias_atraso = max(0, hoy − fecha_vencimiento)      si saldo > 0
estado      = PAGADA         si saldo = 0
              PENDIENTE      si pagado = 0 y hoy ≤ fecha_vencimiento
              PAGO_PARCIAL   si 0 < pagado < monto y hoy ≤ fecha_vencimiento
              VENCIDA        si saldo > 0 y 0 < dias_atraso < umbral_alerta
              MOROSA         si saldo > 0 y dias_atraso ≥ umbral_alerta (7) → alerta al dueño
```

Una cuota vencida o morosa que tiene abonos muestra también el **saldo pendiente** y la marca "con pago parcial".
[PREGUNTA C1-Q-60: con un pago parcial, ¿la alerta de 7 días sigue contándose desde el vencimiento original? Propuesta: sí.]

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
También cuenta el historial de contratos anteriores (si el inquilino regresa). [PREGUNTA C1-Q-25: validar los criterios y los pesos]

### B6. Vacancia (nueva en C1-P-09)

El proceso vigente descuenta la vacancia del ingreso neto, pero falta la fórmula. Propuesta a validar:

```
Vacancia del período = meses sin contrato × alquiler de referencia
Ingreso neto         = ingreso cobrado − impuestos − mantenimiento no trasladado
```

Si el ingreso ya es **cobrado**, la vacancia ya está reflejada: restarla otra vez sería contarla dos veces. Se muestra como dato
informativo y se resta solo en el rendimiento **proyectado** ([C1-Q-17](08-preguntas-abiertas.md)).

### B7. Cálculos de otras verticales [MAPEO]

```
Liquidación a propietario (1.1) = alquiler cobrado − comisión de administración − gastos de reparación
Cuota de gastos comunes (1.2)   = total de gastos × alícuota de la unidad
ROI por unidad (1.3)            = (ingresos de la unidad − costos de la unidad) / inversión en la unidad
Exceso de kilometraje (1.3)     = max(0, km recorridos − km incluidos) × tarifa por km
Ingreso por m² (1.4)            = ingreso del período / m² disponibles
```

### B8. Indicadores del tablero: cobranza y ocupación

Respuesta del cliente (P6, [NUC-Q-26](../../../general/01-analisis-negocio/08-preguntas-abiertas.md)) [CONFIRMADO]: la tarjeta muestra
los **ingresos efectivamente cobrados**; en el inmobiliario la meta es que **todas las unidades estén alquiladas**.

```
Cobrado del mes      = Σ pagos verificados con fecha de pago dentro del mes
Avance de cobranza % = cobrado del mes / meta mensual de cobranza × 100
Ocupación %          = unidades ocupadas / unidades alquilables × 100
Semáforo             = Verde si avance ≥ 100 % y ocupación = 100 %
                       Rojo  si falta cobrar o hay alguna unidad libre
```

- Al hacer clic en rojo se ven **dos listas**: las cuotas pendientes (con saldo) y las **unidades libres**.
- La **meta mensual de cobranza** se propone igual a la suma de los alquileres vigentes con **todas las unidades ocupadas**, de
  modo que una unidad libre baja el avance por sí sola [PROPUESTO → C1-Q-59].
- Las unidades que no se pueden alquilar (en obra, en mantenimiento) no cuentan como alquilables (C1-RN-32).
- Solo el dueño ve este indicador (NUC-RN-30).
