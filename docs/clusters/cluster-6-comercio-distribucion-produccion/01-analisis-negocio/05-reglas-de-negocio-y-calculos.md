# 05. Reglas de negocio y cálculos

> **Hipótesis sin validar.** Los métodos de costeo y los libros exigidos **deben validarse con un contador**.

## Reglas

| ID | Regla | Vertical | Origen |
|----|-------|:--------:|--------|
| C6-RN-01 | **El stock no se edita:** resulta de sumar los movimientos del Kardex. | Todas | Aplica NUC-RN-01 |
| C6-RN-02 | Todo ajuste de stock tiene motivo, responsable y aprobación. | Todas | [INFERIDO] |
| C6-RN-03 | Vender sin stock se bloquea o se permite según el negocio; es un parámetro. | Todas | [INFERIDO] |
| C6-RN-04 | El método de costeo se elige al inicio y no cambia sin un proceso formal. | Todas | [INFERIDO] |
| C6-RN-05 | La venta guarda el costo y el precio del momento; cambios posteriores no la alteran. | Todas | Aplica NUC-RN-01 |
| C6-RN-06 | Una venta no se elimina: se anula con nota de crédito y se revierte el stock. | Todas | [INFERIDO] |
| C6-RN-07 | Si el cliente supera su línea o tiene facturas vencidas, **se bloquea el pedido**. | 6.1 | [MAPEO] |
| C6-RN-08 | La comisión se calcula sobre lo **cobrado**. | 6.1 | [MAPEO] |
| C6-RN-09 | Se despacha primero lo que vence antes. | 6.1 | [INFERIDO] |
| C6-RN-10 | Sin seña no entra a producción; sin saldo no se despacha. Los % son parámetros. | 6.2 | [MAPEO] |
| C6-RN-11 | La venta en caja se verifica por **cierre de turno**, no pago por pago. | 6.3 | [EQUIPO] |
| C6-RN-12 | Una receta tiene versión, con vigencia por fecha. | 6.3 | [EQUIPO] |

## Cálculos

```
Stock actual        = Σ entradas − Σ salidas ± ajustes
Costo promedio      = (stock × costo actual + cantidad comprada × costo de compra) / (stock + cantidad comprada)
CMV del período     = Σ (cantidad vendida × costo de la venta)
Margen bruto %      = (ventas − CMV) / ventas × 100
Valor del inventario = Σ (stock × costo promedio)
Crédito disponible  = línea de crédito − saldo pendiente
Antigüedad de saldos: clasifica por días vencidos en 0–30, 31–60, 61–90, > 90
Costo de plato (6.3) = Σ (cantidad del insumo en la receta × costo del insumo)
Merma (6.3)          = consumo teórico por receta frente a consumo real por conteo
```

**Ejemplo de costo promedio**

| Evento | Cantidad | Costo unit. | Stock | Costo promedio |
|--------|---------:|------------:|------:|---------------:|
| Saldo inicial | 100 | S/ 10.00 | 100 | S/ 10.00 |
| Compra | 50 | S/ 13.00 | 150 | S/ 11.00 |
| Venta a S/ 15 | − 30 | | 120 | S/ 11.00 |

Margen de esa venta: 30 × (15 − 11) = **S/ 120 (26.7 %)**. Con el último costo de compra (S/ 13) parecería S/ 60: es el error típico sin Kardex.

**Ejemplo de conversión:** 1 Caja = 12 unidades. Comprar por caja y vender por unidad exige un factor de conversión y una unidad base para el stock.
