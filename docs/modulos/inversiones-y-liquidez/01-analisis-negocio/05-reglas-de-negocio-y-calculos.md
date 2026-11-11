# 05. Reglas de negocio y cálculos

> Propuesta basada en lo que explicó el cliente. Los números son ilustrativos.
> Los temas tributarios **deben validarse con un contador** antes de implementarlos.

| ID | Regla | Origen |
|----|-------|--------|
| INV-RN-17 | El impuesto se calcula **solo sobre las ganancias**; si hay pérdida, no se paga. | [CONFIRMADO] |
| INV-RN-30 | El sistema solo **calcula y reporta**. Tasa y exoneración son parámetros. | [INFERIDO de la reunión] |
| INV-RN-31 | El rendimiento de una operación se **anualiza con regla de tres** (proporción lineal según los días que duró), no con interés compuesto. | [CONFIRMADO — cuestionario P13, 11/Nov/2026] |
| INV-RN-32 | Si la acción pagó **utilidades o dividendos** durante el período, se suman a la ganancia. | [CONFIRMADO — P13] |
| INV-RN-33 | Hay inversiones en **soles (S/)** y en **dólares (US$)**. Cada cuenta, depósito u operación guarda su moneda y nunca se mezcla sin un tipo de cambio registrado. | [CONFIRMADO — P14] |
| INV-RN-34 | **No** se muestra ganancia estimada ("en papel") de acciones que aún no se venden: solo cuenta la ganancia **realizada**. | [CONFIRMADO — P14] |

## Cálculos

### INV-C1. Cuenta bancaria
```
Interés anual estimado = saldo × TEA
Rendimiento %          = TEA
Plazo                  = indefinido
```

### INV-C2. Depósito a plazo fijo (convención de 360 días, usada por la banca peruana)
```
Interés = monto × ((1 + TEA)^(días / 360) − 1)
```
Ejemplo: S/ 100 000 al 7 % TEA por 180 días → 100 000 × (1.07^0.5 − 1) = **S/ 3 440.80**.
Alerta X días antes de la fecha de vencimiento.

### INV-C3. Operación bursátil (trading)

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
> costos **se restan**, así que el neto debería ser menor. Hay que confirmarlo con el cliente (INV-Q-27).
> Tampoco quedó claro si el bróker cobra **2 %** o **0.2 %** (INV-Q-27).

### INV-C4. Rendimiento de una acción, anualizado y con utilidades (método del cliente)

Respuesta del cliente (P13) [CONFIRMADO]: se compra a un valor **x**, después de un tiempo **t** se vende a un precio **y**;
la ganancia del período es **y − x** y el rendimiento es esa ganancia entre **x**. Con **regla de tres** se lleva a un año, y
si hubo **utilidades** se añaden.

```
Ganancia del período t      = y − x + utilidades o dividendos cobrados en t
Rendimiento del período %   = ganancia del período / x × 100
Rendimiento anual %         = rendimiento del período % × 365 / días de t        (regla de tres, lineal)
Ganancia anual equivalente  = ganancia del período × 365 / días de t
```

- **x** e **y** son el **costo real de compra** y el **ingreso neto de venta** de INV-C3 (con comisiones) [INFERIDO → INV-Q-42].
- Base de **365 días** [INFERIDO → INV-Q-42].
- ~~Ganancia no realizada~~: el cliente **no** la quiere ver (P14, INV-RN-34). Solo cuentan las acciones vendidas.

**Ejemplo con las cifras de la reunión:** compra real S/ 3 840, venta neta S/ 3 950, mantenida **90 días**, sin utilidades:

```
Ganancia del período = 3 950 − 3 840 = S/ 110
Rendimiento período  = 110 / 3 840 = 2.86 %
Rendimiento anual    = 2.86 % × 365 / 90 = 11.62 %
```

El cliente quiere comparar el **% anual** de cada acción (por ejemplo, 3 %, 7 %, 17 %) entre sí y con un plazo fijo para
decidir dónde poner el dinero. Anualizar con regla de tres hace comparables operaciones de distinta duración.

> Nota para el equipo: una operación muy corta con una ganancia pequeña puede dar un % anual muy alto (por ejemplo, 1 % en
> 3 días ≈ 122 % anual). Conviene mostrar siempre los días junto al % anual.

### INV-C5. Resumen y rendimiento ponderado de la cartera
```
Total invertido = Σ cuentas + Σ plazos fijos + Σ bolsa            (por moneda)
Rendimiento ponderado % = Σ (monto_k × rendimiento_k) / total invertido
```

**Monedas (P14)** [CONFIRMADO]: hay inversiones en **soles** y en **dólares**. Los totales se muestran **por moneda**
(un total en S/ y otro en US$). Para un total consolidado y un rendimiento ponderado de toda la cartera, los montos en US$
se convierten a S/ con un **tipo de cambio que ingresa el dueño** [PROPUESTO → INV-Q-20]. Los rendimientos % de cada
instrumento se calculan en su moneda de origen (no se mezclan con la variación del tipo de cambio).

### INV-C6. Reporte tributario anual (ganancias de capital)
```
Ganancia neta del año = Σ ganancias − Σ pérdidas   (operaciones realizadas en el año)
Impuesto estimado     = max(0, ganancia neta − exoneración aplicable) × 5 %
```
> **Validar con contador:** para personas naturales domiciliadas, la ganancia de capital por venta de
> valores tributa un **5 % efectivo**. Existe o ha existido una **exoneración de las primeras 5 UIT** para
> valores negociados en la BVL bajo ciertas condiciones. El sistema solo debe **calcular y reportar**;
> la tasa y la exoneración deben ser **parámetros configurables**.
>
> **Operaciones en dólares (P14):** para el reporte tributario las ganancias en US$ deben expresarse en soles. Qué tipo de
> cambio usar (el del día de cada operación u otro) debe definirlo el contador [PREGUNTA INV-Q-43].
