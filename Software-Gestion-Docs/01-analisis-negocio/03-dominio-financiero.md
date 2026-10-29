# 03. Dominio financiero (inversiones)

## 3.1 Descripción del negocio

Es un negocio **100 % digital** (sin activos físicos ni mantenimiento). El cliente tiene su
dinero repartido en tres tipos de instrumentos y quiere ver **cuánto tiene en cada uno y
cuánto rinde (%)**, para decidir dónde moverlo ("este instrumento rinde 3 %: lo mato y lo paso
al que rinde más").

Además, a fin de año necesita un **reporte de ganancias de trading** para declarar y pagar el
**impuesto a la renta** (solo sobre ganancias; si hay pérdidas, no paga).

## 3.2 Instrumentos

### A) Cuentas bancarias (de ahorro con rendimiento)
- Banco, tipo de cuenta, moneda (S/ o US$) [PREGUNTA P20], **saldo** y **tasa (TEA)** (por ejemplo, 5 %).
- **Plazo: indefinido.** El dinero se puede retirar en cualquier momento.

### B) Depósitos a plazo fijo
- Entidad (banco o caja), monto, moneda, **TEA** (por ejemplo, 7–9 %), **fecha de apertura** y **fecha de vencimiento** (ejemplo dado: 11/12/2037).
- En la fecha de vencimiento hay que retirar o renovar → **alerta de vencimiento** [INFERIDO].
- Referencia de mercado: el cliente usa **comparabien.com** para comparar tasas (en la reunión salieron TEA de 5.3–5.8 % para S/ 500 000 en Lima).

### C) Bolsa de Valores de Lima (BVL)
- Acciones de distintas empresas (mencionó BCP / Credicorp y otras; por ejemplo, "Puerto"). [INFERIDO]
- Se opera a través de un **bróker** (por ejemplo, Trii o Renta 4) que cobra comisión.
- **Operaciones**: compra y venta, con:
  - **Precio de bolsa** (por ejemplo, compra a 3.74).
  - **Costo real** (precio + comisión del bróker + costos de bolsa + IGV; por ejemplo, 3.84).
  - Igual en la venta (precio de bolsa 4.05; **venta real** neta de costos).
- **Utilidades / dividendos** que reparte la empresa a los accionistas → también suman al rendimiento.
- El cliente prefiere que el % de una acción se calcule sobre las **utilidades o beneficios totales** frente a lo invertido, no solo sobre la diferencia de precio [PREGUNTA P21].

## 3.3 Lo que el sistema debe mostrar

| Vista | Contenido |
|-------|-----------|
| **Resumen financiero** | Monto en cuentas + monto en plazos fijos + monto en bolsa = **total** (por ejemplo, S/ 300 000), con su rendimiento promedio ponderado |
| **Por instrumento** | Monto, % de rendimiento, plazo (indefinido o fecha de vencimiento), ganancia esperada o realizada |
| **Ranking** | Ordenar los instrumentos por rendimiento, para identificar los que rinden menos |
| **Reporte tributario anual** | Ganancias y pérdidas realizadas de trading en el año, base imponible e impuesto estimado |
| **Comparación con el inmobiliario** | El rendimiento de cada inmueble frente a la tasa de un plazo fijo [INFERIDO; el cliente hizo esta comparación en la reunión] |

## 3.4 Entidades preliminares

- **Entidad financiera** (banco, caja, bróker).
- **Cuenta bancaria**: saldo, TEA y movimientos o actualizaciones de saldo [PREGUNTA P22: ¿se registran movimientos o solo saldos actualizados a mano?].
- **Depósito a plazo**: monto, TEA, fechas e interés esperado.
- **Acción / Valor**: emisor, ticker (nemónico BVL), moneda.
- **Operación bursátil**: tipo (compra o venta), fecha, cantidad, precio de bolsa, comisiones, impuestos y monto real.
- **Posición**: cantidad en cartera y costo promedio [INFERIDO].
- **Dividendo / Utilidad recibida**: fecha, acción y monto.
- **Objetivo financiero** del negocio, para el tablero.

## 3.5 Fuera de alcance inicial (sugerido)

- La conexión automática con bancos o brókers para importar saldos y operaciones (no suele haber APIs públicas). En las etapas 1 y 2 el **registro es manual**, con importación de Excel o CSV como posible mejora.
- Precios de acciones en tiempo real (la valorización de la cartera abierta se haría con el último precio que ingrese el usuario) [PREGUNTA P23].
