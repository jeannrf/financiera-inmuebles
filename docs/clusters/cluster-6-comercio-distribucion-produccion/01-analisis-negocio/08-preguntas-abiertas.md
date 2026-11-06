# 08. Preguntas abiertas

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

⭐ = bloquea el diseño.

## Comunes

| ID | Pregunta |
|----|----------|
| C6-Q-01 ⭐ | ¿Cuántas ventas por día y cuántos productos tienen? Define la arquitectura |
| C6-Q-02 ⭐ | ¿Qué método de costeo exige su contador: promedio o PEPS? (validar) |
| C6-Q-03 | ¿Se permite vender sin stock? |
| C6-Q-04 | ¿Tienen varias tiendas o almacenes? |
| C6-Q-05 | ¿Ya usan un proveedor de facturación electrónica? |

## Por vertical

| ID | Vertical | Pregunta |
|----|:--------:|----------|
| C6-Q-10 | 6.1 | ¿Quién puede liberar un pedido bloqueado? ¿Hay un monto de tolerancia? |
| C6-Q-11 | 6.1 | ¿Los preventistas venden sin señal? ¿Cuánto tiempo? |
| C6-Q-12 | 6.1 | ¿La comisión se reduce si el cobro es tardío? |
| C6-Q-20 | 6.2 | ¿Qué tan complejas son las reglas del cotizador? ¿Es posible expresarlas por metadatos? |
| C6-Q-21 | 6.2 | ¿Fabrican o subcontratan? |
| C6-Q-30 ⭐ | 6.3 | Ya se decidió que van en este clúster. ¿Tiendas y restaurantes usan **una sola plantilla** o dos? Comparten caja, proveedores y stock, pero el restaurante agrega mesas, comandas y recetas |
| C6-Q-31 ⭐ | 6.3 | ¿Qué debe hacer la caja si no hay internet? (validar exigencias de SUNAT sobre contingencia) |
| C6-Q-32 | 6.3 | ¿Qué hardware usan: impresora de tickets, lector, cajón? |
