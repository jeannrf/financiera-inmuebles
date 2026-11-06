# 05. Reglas de negocio y cálculos

> Propuesta basada en lo que explicó el cliente. Los números son ilustrativos.
> Los temas tributarios **deben validarse con un contador** antes de implementarlos.

| ID | Regla | Origen |
|----|-------|--------|
| INV-RN-17 | El impuesto se calcula **solo sobre las ganancias**; si hay pérdida, no se paga. | [CONFIRMADO] |
| INV-RN-30 | El sistema solo **calcula y reporta**. Tasa y exoneración son parámetros. | [INFERIDO de la reunión] |

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

### INV-C4. Rendimiento de una acción incluyendo utilidades o dividendos (preferencia del cliente)
```
Rendimiento total % = (ganancias realizadas + dividendos/utilidades recibidos + ganancia no realizada [INV-Q-23]) / inversión total × 100
```
El cliente quiere comparar el % de cada acción (por ejemplo, 3 %, 7 %, 17 %) para decidir de cuál salir.

### INV-C5. Resumen y rendimiento ponderado de la cartera
```
Total invertido = Σ cuentas + Σ plazos fijos + Σ bolsa
Rendimiento ponderado % = Σ (monto_k × rendimiento_k) / total invertido
```

### INV-C6. Reporte tributario anual (ganancias de capital)
```
Ganancia neta del año = Σ ganancias − Σ pérdidas   (operaciones realizadas en el año)
Impuesto estimado     = max(0, ganancia neta − exoneración aplicable) × 5 %
```
> **Validar con contador:** para personas naturales domiciliadas, la ganancia de capital por venta de
> valores tributa un **5 % efectivo**. Existe o ha existido una **exoneración de las primeras 5 UIT** para
> valores negociados en la BVL bajo ciertas condiciones. El sistema solo debe **calcular y reportar**;
> la tasa y la exoneración deben ser **parámetros configurables**.
