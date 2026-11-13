# 01. Contexto y objetivos

## 1.1 Por qué no es un clúster

Un clúster agrupa negocios que **venden algo a sus clientes**. Aquí no hay clientes, ventas ni cobranza: el dueño
gestiona **su propio dinero** repartido entre cuentas, plazos fijos y acciones. Además, cualquier empresario de cualquier clúster podría querer
gestionar su liquidez.

Por eso es un **módulo complementario**, que se puede agregar a una organización sin importar sus negocios. Se muestra como una tarjeta más en el tablero.

Si en el futuro se atiende a sociedades de inversión o se ofrece a terceros, habría que reevaluar si merece ser un clúster.

## 1.2 Problema

El cliente piloto tiene dinero repartido en varias entidades y no ve de un vistazo cuánto rinde cada instrumento.
A fin de año necesita calcular a mano las ganancias de trading para su impuesto.

## 1.3 Objetivos

| ID | Objetivo |
|----|----------|
| OE-INV-01 | Consolidar los instrumentos con su monto y rendimiento % |
| OE-INV-02 | Ordenar los instrumentos por rentabilidad para decidir dónde mover el dinero |
| OE-INV-03 | Alertar los vencimientos de plazos fijos |
| OE-INV-04 | Generar el reporte anual de ganancias para el impuesto a la renta |
| OE-INV-05 | Ofrecer una tasa de referencia para comparar con los negocios (por ejemplo, Cap Rate en C1) |

## 1.4 Relación con otras piezas

- **Núcleo:** usa usuarios, alertas, documentos y tablero.
- **Clúster 1:** ~~C1-P-09 lee su tasa ponderada, si está activo.~~ **Actualizado (13/Nov/2026):** el piloto compara el rendimiento inmobiliario con una **tasa media de plazo fijo que ingresa el analista** (C1-RN-49). C1 ya no depende de este módulo.
- No se mezcla con **Finanzas y Tesorería** del núcleo: esta registra la caja de la operación de un negocio; este módulo, las inversiones del dueño.
