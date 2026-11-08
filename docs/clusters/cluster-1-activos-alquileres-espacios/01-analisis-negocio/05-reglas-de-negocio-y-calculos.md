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
| C1-RN-06 | Un pago con atraso de **≥ 7 días** (valor configurable) genera una alerta al **dueño** por correo o SMS. | [CONFIRMADO; el cliente dijo 5 y 7 días → C1-Q-13] |
| C1-RN-07 | El analista recibe **cada semana** la lista de cobros de la semana. | [CONFIRMADO] |
| C1-RN-08 | Una **mejora siempre se suma** al costo o valor del inmueble. | [CONFIRMADO] |
| C1-RN-09 | El valor del inmueble se actualiza automáticamente con la **UIT** cada año. | [CONFIRMADO] |
| C1-RN-10 | En el prorrateo de servicios **no puede haber pérdida ni ganancia**: la suma cobrada a los departamentos es igual al total del recibo. | [CONFIRMADO] |
| C1-RN-14 | Si un inquilino no cumple su turno de limpieza, se contrata un reemplazo y **se le cobra** el costo. | [CONFIRMADO] |
| C1-RN-16 | No hay descuentos por pronto pago ni por cumpleaños. | [CONFIRMADO] "No hay descuento" |
| C1-RN-19 | Un inquilino con deudas no puede finalizar su contrato sin liquidación. | [Proceso C1-P-11] |

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
| C1-RN-37 | Una penalidad por mora o el ajuste por IPC son **parámetros por vertical**: el mapeo los incluye en 1.1, mientras que el piloto aún no define si cobra mora ([C1-Q-24](08-preguntas-abiertas.md)) y usa incrementos manuales. | 1.1 |
| C1-RN-38 | La alerta de morosidad escala: analista (N₁ días) → dueño (N₂ días). N₁ y N₂ son parámetros. El dueño recibe el nivel 2 aunque el analista no haya hecho nada. | [CONFIRMADO — PPT cliente] + [PREGUNTA C1-Q-56] |

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

Hay **dos métodos** posibles; el cliente usó ambos según el ejemplo. Hay que confirmar cuál (C1-Q-19).

**Método A, proporcional (garantiza C1-RN-10):**
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
- como cargo de "áreas comunes" dentro del mantenimiento. [PREGUNTA C1-Q-19]

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
[PREGUNTA C1-Q-24: ¿se aceptan **pagos parciales**? ¿Hay **mora o penalidad** por atraso?]

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
