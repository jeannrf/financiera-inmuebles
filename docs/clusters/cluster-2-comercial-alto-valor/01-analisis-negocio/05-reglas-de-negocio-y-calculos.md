# 05. Reglas de negocio y cálculos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Reglas

| ID | Regla | Vertical | Origen |
|----|-------|:--------:|--------|
| C2-RN-01 | Una cotización enviada no se edita: cada cambio crea una versión. | Todas | Aplica NUC-RN-01 |
| C2-RN-02 | Las oportunidades pertenecen a la empresa, no al vendedor. | Todas | [INFERIDO] |
| C2-RN-03 | Un descuento sobre el límite requiere aprobación. | Todas | [INFERIDO] |
| C2-RN-04 | La anulación de una venta genera un ajuste de comisión en contra. | Todas | [INFERIDO] |
| C2-RN-05 | La prima **no es ingreso** del bróker; el ingreso es la comisión. | 2.1 | [INFERIDO] |
| C2-RN-06 | Lo cedido a sub-agentes no puede superar lo recibido, salvo excepción aprobada. | 2.1 | [INFERIDO] |
| C2-RN-07 | Alertas de renovación a los 60, 30 y 15 días. | 2.1 | [MAPEO] |
| C2-RN-08 | Un vehículo en consignación no forma parte del activo del negocio. | 2.2 | [INFERIDO] |
| C2-RN-09 | Un vehículo se vende una sola vez; una reserva bloquea el inventario. | 2.2 | [INFERIDO] |
| C2-RN-10 | Cobro por hitos: cada hito requiere su condición (por ejemplo, acta de conformidad). | 2.3 | [MAPEO] |
| C2-RN-11 | Cada operación multimoneda guarda el tipo de cambio aplicado. | 2.4 | [INFERIDO] |

## Cálculos

```
Forecast del mes         = Σ (monto de la oportunidad × probabilidad de su etapa)

Margen de vehículo (2.2) = precio de venta − costo de adquisición − gastos de alistamiento − comisión del vendedor   [MAPEO]

Liquidación consignación = precio de venta − comisión pactada − gastos autorizados

Comisión neta del bróker = comisión de la aseguradora − comisión cedida al sub-agente

Desviación de obra (2.3) = costo real de instalación − costo presupuestado                                          [MAPEO]

Utilidad por viaje (2.4) = total cobrado − Σ pagos a proveedores (en moneda base)                                   [MAPEO]
```

**Ejemplo del forecast:**

| Oportunidad | Monto | Etapa | Prob. | Esperado |
|-------------|------:|-------|:-----:|---------:|
| A | S/ 40 000 | Propuesta | 50 % | S/ 20 000 |
| B | S/ 25 000 | Negociación | 80 % | S/ 20 000 |
| C | S/ 90 000 | Calificado | 20 % | S/ 18 000 |
| **Total** | | | | **S/ 58 000** |

Las probabilidades son parámetros por negocio; luego conviene ajustarlas con datos reales de cierre.
