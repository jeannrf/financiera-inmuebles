# 06. Requerimientos preliminares

Prioridad **MoSCoW**. La columna **Etapa** remite a [07-fases-y-alcance.md](07-fases-y-alcance.md).

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| INV-RF-60 | Registrar cuentas bancarias (entidad, moneda, saldo, TEA) | M | 2 |
| INV-RF-61 | Registrar plazos fijos (monto, TEA, apertura, vencimiento) y calcular el interés esperado | M | 2 |
| INV-RF-62 | Alerta de vencimiento de plazo fijo | S | 2 |
| INV-RF-63 | Registrar operaciones de bolsa (compra y venta, cantidad, precio, comisiones, impuestos) | M | 2 |
| INV-RF-64 | Registrar dividendos o utilidades recibidos | S | 2 |
| INV-RF-65 | Calcular la ganancia o pérdida y el rendimiento % por operación, por acción y total | M | 2 |
| INV-RF-66 | Resumen financiero: total por tipo de instrumento, rendimiento ponderado y ranking | M | 2 |
| INV-RF-67 | **Reporte anual** de ganancias de capital para el impuesto a la renta | M | 2 |
| INV-RF-68 | Activar el módulo por organización, con su propia tarjeta en el tablero | M | 2 |
| INV-RF-69 | Publicar la tasa ponderada para otros paquetes, como C1 | S | 2 |
| INV-RF-70 | Mostrar la ganancia o pérdida **mensual y anual** del módulo (además de por operación) [CONFIRMADO — PPT cliente] | M | 2 |
| INV-RF-71 | Registrar y guardar el **EBITDA trimestral** (ver [INV-Q-39](08-preguntas-abiertas.md) sobre de qué entidad) [CONFIRMADO — PPT cliente] | S | 2 |
| INV-RF-72 | **Alerta por teléfono** cuando el precio de una acción en cartera varíe **±5 %** (umbral configurable) [CONFIRMADO — PPT cliente] | S | 3 (o 2 si se elige la opción manual) |
| INV-RF-73 | Mostrar por cada acción el costo a **precio de bolsa (BV)** y el **costo real** con comisiones [CONFIRMADO — PPT cliente] | M | 2 |
| INV-RF-86 | Importación automática desde bancos o brókers y precios de bolsa en línea | W | Futuro |

> INV-RF-73 ya está cubierto por el cálculo INV-C3; esta fila solo lo hace explícito porque el cliente lo pidió así en la PPT.

> **Conflicto con el alcance:** INV-RF-72 necesita precios actualizados, y las cotizaciones de bolsa en tiempo real están
> **fuera de alcance** ([§7.4 general](../../../general/01-analisis-negocio/07-fases-y-alcance.md), INV-RF-86). Opciones:
> (a) el analista actualiza el precio a mano y la alerta se evalúa al guardar; (b) un precio de cierre diario de una fuente
> gratuita en la etapa 3. Pendiente en [INV-Q-40](08-preguntas-abiertas.md); no se cambia §7.4 sin decisión.