# 02. Dominio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 2.1 Modelo común del clúster [INFERIDO]

```
Producto (SKU) ── Unidades de medida, lotes, costo
│
├── Almacén → Movimientos de stock (Kardex): entradas, salidas, ajustes, traslados
│
├── Compra: Orden de compra → Recepción → Costo → Cuenta por pagar
│
└── Venta: Pedido (con lista de precios) → Despacho → Comprobante
                                                └── Cuenta corriente del cliente → Pagos
```

| Concepto común | 6.1 Mayoristas | 6.2 A medida | 6.3 Minorista y restaurantes [EQUIPO] |
|----------------|----------------|--------------|------------------------------------------|
| **Volumen** | Medio | Bajo | **Muy alto** |
| **Producto** | Catálogo fijo, por lote | Configurable | Catálogo fijo; platos con receta |
| **Venta** | Pedido del vendedor en ruta | Cotización a medida | Ticket en caja o comanda |
| **Cobro** | Crédito | Anticipo + saldo | Contado |
| **Stock** | Múltiples almacenes | Materia prima | Tienda; insumos que se descuentan por receta |
| **Riesgo principal** | Crédito | Desviación de costos | Mermas y diferencias de caja |

## 2.2 Especificación por vertical (del mapeo)

*Orientado a la compraventa de bienes físicos donde el control de inventario, listas de precios, crédito comercial y órdenes de pedido son el centro del negocio.*

### Arquitectura del clúster
* **Entidad Principal:** Pedido de Venta / Orden de Compra + Catálogo de Productos (SKU).
* **Sub-entidades:** Almacenes/Depósitos, Movimientos de Stock (Kardex), Listas de Precios, Cuentas Corrientes de Clientes.
* **Conexión Financiera (P&L):** Costo de Mercadería Vendida (CMV / COGS), valorización de inventario en tiempo real y antigüedad de saldos de cuentas por cobrar.

### Verticales

#### 6.1. Distribuidoras Mayoristas y Comercializadoras B2B (Alimentos, Ferretería, Insumos)
* **Cobertura Operativa:**
  * Catálogo de productos con múltiples unidades de medida (Unidad, Caja, Pallet), control de lotes/fechas de vencimiento y stock mínimo de reposición.
  * Múltiples listas de precios (Mayorista, Distribuidor, Minorista, Promocional) y toma de pedidos por vendedores en ruta o preventistas.
  * Gestión de despacho: Preparación de pedidos (Picking), hoja de ruta por transportista y control de mercadería devuelta o rechazada en entrega.
* **Cobertura Financiera:** Gestión de línea de crédito por cliente (bloqueo automático de pedidos si supera el límite de deuda o tiene facturas vencidas), comisiones de vendedores sobre monto efectivamente **cobrado** (no solo facturado).

#### 6.2. Mueblerías, Carpinterías, Cerramientos y Equipamiento a Medida (Make-to-Order)
* **Cobertura Operativa:**
  * Cotizador de productos configurables (medidas personalizadas, tipo de material, tapizado, color, herrajes).
  * Conversión automática de la Venta en una **Orden de Producción/Fabricación** para el taller propio o en una **Orden de Compra** al proveedor/fábrica.
  * Pipeline de seguimiento: Pedido confirmado → En fabricación → Control de calidad → En almacén listo para envío → Programación de entrega e instalación.
* **Cobertura Financiera:** Gestión de señas/anticipos de clientes (ej. 60% para iniciar fabricación y 40% antes de despachar), costeo de materia prima consumida por orden y control de rentabilidad por pedido fabricado.

#### 6.3. Comercio Minorista y Restaurantes (Punto de Venta) [EQUIPO]

*Esta vertical no estaba en el documento de mapeo. Se añade porque restaurantes y tiendas comparten con el clúster muchas ventas, proveedores e inventario ([decisión NUC-Q-02](../../../general/01-analisis-negocio/08-preguntas-abiertas.md#decisiones-tomadas)). Su detalle aún es una hipótesis por validar.*

* **Cobertura Operativa:**
  * Punto de venta rápido, con código de barras, turnos de caja y varios métodos de pago por ticket.
  * Tienda: catálogo con variantes, promociones y reposición por stock mínimo.
  * Restaurante: mesas y comandas enviadas a cocina, **recetas** que descuentan insumos por cada plato vendido, y control de mermas.
* **Cobertura Financiera:** Cierre de caja por turno, emisión de boleta y factura electrónica en el momento de la venta, costo por plato o producto y margen por categoría.
