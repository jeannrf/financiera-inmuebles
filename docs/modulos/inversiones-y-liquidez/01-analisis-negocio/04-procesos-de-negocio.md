# 04. Procesos de negocio

## INV-P-12. Consolidación de portafolio y reporte tributario
**AS-IS:** Dinero distribuido en múltiples entidades sin métricas consolidadas de rendimiento ni cálculo de impuestos por trading.
**TO-BE:**
1. El **Dueño** registra o actualiza los saldos de sus instrumentos: cuentas bancarias de ahorro (con tasa TEA), depósitos a plazo fijo (monto, TEA, fecha de vencimiento) y operaciones bursátiles en la BVL (compras/ventas incorporando comisiones del bróker e IGV).
2. El sistema calcula el rendimiento % individual y el rendimiento promedio ponderado del portafolio, estructurando un **Ranking de Rentabilidad**.
3. Emite alertas automáticas ante el próximo vencimiento de un depósito a plazo fijo.
4. Al cierre del año fiscal, genera el **Reporte de Ganancias de Capital y Trading**, determinando la base imponible neta para el pago del Impuesto a la Renta de segunda categoría / capital.

> **Actualización:** C1-P-09 usa la tasa ponderada de este proceso para comparar inmuebles y plazos fijos.
