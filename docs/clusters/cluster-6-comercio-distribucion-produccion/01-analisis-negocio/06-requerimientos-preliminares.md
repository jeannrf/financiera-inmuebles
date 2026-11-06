# 06. Requerimientos preliminares

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Comunes

| ID | Requerimiento | Prioridad |
|----|---------------|:---------:|
| C6-RF-01 | Catálogo con SKU y múltiples unidades de medida | M |
| C6-RF-02 | Múltiples almacenes y traslados | S |
| C6-RF-03 | Kardex con movimientos inmutables | M |
| C6-RF-04 | Costo promedio y CMV | M |
| C6-RF-05 | Órdenes de compra y recepción | M |
| C6-RF-06 | Stock mínimo y sugerencia de reposición | S |
| C6-RF-07 | Pedidos y ventas con lista de precios | M |
| C6-RF-08 | Comprobantes electrónicos (usa NUC-RF-38) | M |
| C6-RF-09 | Notas de crédito y devoluciones | M |
| C6-RF-10 | Cuentas corrientes y antigüedad de saldos | M |
| C6-RF-11 | Inventario físico con ajustes aprobados | M |
| C6-RF-12 | Valor del inventario en tiempo real | S |

## Por vertical

| ID | Requerimiento | Vertical | Prioridad |
|----|---------------|:--------:|:---------:|
| C6-RF-20 | Lotes y vencimientos | 6.1 | M |
| C6-RF-21 | Listas de precios múltiples | 6.1 | M |
| C6-RF-22 | Toma de pedidos en ruta | 6.1 | S |
| C6-RF-23 | Picking, hoja de ruta y rechazos | 6.1 | S |
| C6-RF-24 | Línea de crédito con bloqueo automático | 6.1 | M |
| C6-RF-25 | Comisión sobre lo cobrado | 6.1 | S |
| C6-RF-30 | Cotizador de productos configurables | 6.2 | M |
| C6-RF-31 | Conversión a orden de producción o compra | 6.2 | M |
| C6-RF-32 | Pipeline de fabricación y entrega | 6.2 | M |
| C6-RF-33 | Señas y saldo antes de despachar | 6.2 | M |
| C6-RF-34 | Costo real de materiales por pedido | 6.2 | S |
| C6-RF-40 | Punto de venta rápido con código de barras | 6.3 | M |
| C6-RF-41 | Turnos y cierre de caja | 6.3 | M |
| C6-RF-42 | Varios métodos de pago por ticket | 6.3 | M |
| C6-RF-43 | Mesas y comandas a cocina | 6.3 | M (restaurante) |
| C6-RF-44 | Recetas que descuentan insumos | 6.3 | M (restaurante) |
| C6-RF-45 | Mermas y costo por plato | 6.3 | S |

## No funcionales propios

| ID | Requerimiento |
|----|---------------|
| C6-RNF-01 | **Alto volumen:** el registro de una venta en caja debe ser casi inmediato, con cargas elevadas por negocio; a definir con un cliente real |
| C6-RNF-02 | **Continuidad:** una caja no puede detenerse por una caída de internet o de la facturación electrónica. Requiere modo de contingencia |
| C6-RNF-03 | **Concurrencia:** dos ventas simultáneas no pueden dejar un stock incoherente |
| C6-RNF-04 | Los volúmenes de un negocio no degradan a otros clientes (ver NUC-RNF-17) |
| C6-RNF-05 | Lectura de código de barras e impresión de ticket desde el navegador o con mínima instalación |
