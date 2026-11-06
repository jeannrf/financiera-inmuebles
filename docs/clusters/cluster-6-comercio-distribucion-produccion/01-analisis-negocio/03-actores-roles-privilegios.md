# 03. Actores, roles y privilegios

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

| Actor | Descripción | Verticales |
|-------|-------------|------------|
| **Dueño / Gerente** | Ve márgenes, precios y crédito | Todas |
| **Vendedor / Preventista** | Toma pedidos en ruta | 6.1, 6.2 |
| **Cajero** | Vende en mostrador y cierra su turno | 6.3 |
| **Mozo** | Toma comandas | 6.3 |
| **Cocina** | Recibe y prepara comandas | 6.3 |
| **Almacenero** | Recibe, prepara y ajusta stock | Todas |
| **Transportista** | Entrega y registra rechazos | 6.1 |
| **Jefe de producción / Taller** | Ejecuta órdenes de producción | 6.2 |
| **Cobranzas / Administración** | Gestiona créditos y cobros | 6.1, 6.2 |
| **Proveedor** | Recibe órdenes de compra, sin acceso | Todas |

Leyenda: ✅ puede · 👁 solo ver · ❌ no puede · ⚠ parcial

| Funcionalidad | Dueño | Vendedor o cajero | Almacén | Cobranzas |
|---------------|:-----:|:-----:|:-----:|:-----:|
| Crear pedidos o ventas | ✅ | ✅ | ❌ | ❌ |
| Ver precio de lista | ✅ | ✅ | ⚠ | ✅ |
| Ver costo y margen | ✅ | ❌ | ❌ | ❌ |
| Cambiar precios | ✅ | ⚠ con límite | ❌ | ❌ |
| Ver stock | ✅ | ✅ | ✅ | 👁 |
| Registrar **ajustes de stock** | ✅ | ❌ | ⚠ con aprobación | ❌ |
| Liberar un cliente bloqueado | ✅ | ❌ | ❌ | ⚠ con límite |
| Registrar cobros | ✅ | ⚠ en caja | ❌ | ✅ |
| Anular una venta | ✅ | ⚠ con autorización | ❌ | ❌ |
| Cerrar turno de caja | ✅ | ✅ propio | ❌ | ❌ |
| Ver comisiones | ✅ todas | ⚠ propias | ❌ | 👁 |
