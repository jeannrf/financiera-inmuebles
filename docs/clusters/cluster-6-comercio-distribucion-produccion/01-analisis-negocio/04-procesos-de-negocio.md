# 04. Procesos de negocio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 4.1 Procesos comunes

### C6-P-01. Catálogo y carga inicial de stock
Se registran productos con unidades de medida y costo. Se carga el stock con un inventario físico y una fecha de corte.

### C6-P-02. Compra y reposición
1. El sistema sugiere reponer lo que cae bajo el mínimo.
2. Se emite la orden de compra.
3. Al recibir, se registra la entrada, se actualiza el costo y se genera la cuenta por pagar.

### C6-P-03. Toma de pedido o venta
El sistema aplica la lista de precios y valida el stock y el crédito del cliente. Al confirmar, reserva stock.

### C6-P-04. Despacho y comprobante
Se prepara el pedido, se descuenta stock y se emite el comprobante electrónico.

### C6-P-05. Cobro y cuenta corriente
Las ventas a crédito generan obligaciones con antigüedad. Los cobros se aplican a documentos. Las alertas reutilizan el núcleo.

### C6-P-06. Inventario físico y ajustes
Conteo físico → Diferencias → Aprobación del dueño → Ajuste en el Kardex con su motivo.

## 4.2 Procesos por vertical

### C6-P-10. Preventa en ruta (6.1) [MAPEO]
El preventista visita, toma pedidos y ve el crédito disponible. Si hay una factura vencida o se supera el límite, **el pedido se bloquea** y requiere liberación.

### C6-P-11. Picking y hoja de ruta (6.1) [MAPEO]
Pedidos → Picking por lote (primero el que vence antes) → Hoja de ruta → Entrega. Lo devuelto o rechazado reingresa al stock o va a merma.

### C6-P-12. Comisión sobre lo cobrado (6.1) [MAPEO]
La comisión se genera cuando el cliente **paga**, y no al facturar.

### C6-P-20. Cotización configurable (6.2) [MAPEO]
Se eligen medidas, material, color y herrajes. El sistema calcula el costo y el precio con reglas. Es versionada.

### C6-P-21. De venta a producción (6.2) [MAPEO]
1. El cliente paga la seña (por ejemplo, 60 %).
2. La venta se convierte en **orden de producción** o de compra a fábrica.
3. Avanza: En fabricación → Control de calidad → Listo → Programar entrega e instalación.
4. Se cobra el saldo **antes de despachar**, y se compara el costo real con el estimado.

### C6-P-30. Venta rápida y turno de caja (6.3) [EQUIPO]
1. El cajero abre turno con un monto inicial.
2. Vende con código de barras o búsqueda, cobra con uno o más métodos y emite el comprobante.
3. Al cierre, cuenta el dinero y el sistema calcula la diferencia. Una diferencia alta alerta al dueño.

### C6-P-31. Comanda y receta (6.3) [EQUIPO]
1. El mozo registra el pedido por mesa, y la comanda llega a cocina.
2. Al cobrar, se cierra la mesa y se emite el comprobante.
3. Cada plato vendido descuenta insumos según su receta. El conteo periódico revela la merma real.
