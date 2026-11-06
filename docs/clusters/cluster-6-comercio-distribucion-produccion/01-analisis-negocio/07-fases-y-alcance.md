# 07. Fases y alcance

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

**Dependencias:** núcleo, motor de **Inventario** (nuevo, grande), **comprobantes electrónicos** y, para 6.3, punto de venta. Es el clúster con **más trabajo nuevo** y conviene llegar con la fábrica probada ([fases generales](../../../general/01-analisis-negocio/07-fases-y-alcance.md#73-qué-clúster-va-después-del-piloto)).

**Vertical de entrada sugerida: 6.2 A medida** [INFERIDO]: tiene poco volumen, un flujo de expediente parecido a C2 y no exige punto de venta ni contingencia. Sirve para construir el Kardex con menos riesgo. **6.3** es el mayor mercado, pero el mayor desafío técnico: conviene abordarla al final.

| Fase | Contenido |
|------|-----------|
| **MVP del clúster** | Catálogo, Kardex, compras, ventas, comprobantes, cuentas corrientes |
| **Vertical de entrada** | Cotizador, señas, orden de producción, costeo real |
| **6.1** | Lotes, listas de precios, crédito con bloqueo, despacho, comisión |
| **6.3** | Punto de venta, turnos, contingencia; luego, mesas, comandas y recetas |

**Fuera de alcance inicial:**

- Planificación de producción con máquinas y capacidad (MRP).
- Tienda en línea y plataformas de delivery.
- Conexión con balanzas o terminales de pago.
- Optimización de rutas.

> **Riesgo a evaluar:** 6.3 compite con productos de punto de venta muy maduros. Antes de construirla, conviene investigar el mercado y definir por qué un cliente nos elegiría. La respuesta probable: la vista consolidada con sus otros negocios.
