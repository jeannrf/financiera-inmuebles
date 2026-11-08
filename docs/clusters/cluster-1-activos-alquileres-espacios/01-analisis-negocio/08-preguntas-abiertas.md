# 08. Preguntas abiertas

> Las marcadas con ⭐ bloquean el diseño y conviene resolverlas primero. Las del piloto deben cerrarse antes del SRS.

## Inmobiliario: inmuebles, contratos y cobros

| ID | Pregunta |
|----|----------|
| C1-Q-10 | ¿El valor se registra por **edificio**, por **departamento** o por ambos? Si es por edificio, ¿cómo se reparte el rendimiento entre los departamentos? |
| C1-Q-11 | ¿Un contrato puede tener **varios inquilinos** (pareja, compañeros)? ¿Quién es el responsable del pago? |
| C1-Q-12 | ¿Qué medios de pago acepta (Yape, Plin, transferencia, efectivo)? ¿Hay depósito de garantía? ¿Cómo se registra y se devuelve? |
| C1-Q-13 ⭐ | La alerta al dueño, ¿a los **5** o a los **7** días de atraso? ¿Quiere SMS, correo o ambos? |
| C1-Q-14 | ¿El saludo de cumpleaños se envía por correo? ¿Con algún texto o diseño en particular? |
| C1-Q-15 | ¿Se puede cerrar un mes si un inquilino quedó como **incobrable**? ¿Se puede **reabrir** un mes cerrado? |
| C1-Q-24 ⭐ | ¿Se aceptan **pagos parciales**? ¿Se cobra **mora o penalidad** por atraso? |
| C1-Q-28 | ¿El día de pago es el mismo para todos o depende de cada contrato? |
| C1-Q-29 | ¿Qué hacer con el contrato al renovarlo: se crea uno nuevo o se extiende el actual? ¿Con cuántos días de anticipación quiere la alerta? |

## Inmobiliario: servicios, mantenimiento y limpieza

| ID | Pregunta |
|----|----------|
| C1-Q-19 ⭐ | Para el prorrateo, ¿se usa el **porcentaje del consumo** sobre el total del recibo, o un **factor (S/ por unidad)** como el 0.87? Si la suma de los submedidores no coincide con el medidor general, ¿cómo se reparte la diferencia? |
| C1-Q-33 | ¿Qué conceptos se cobran como mantenimiento (vigilancia, ascensor, luz común, limpieza)? ¿Es un monto fijo o se reparte según los gastos del mes? |
| C1-Q-34 | ¿El gas también se prorratea? **Respondida: sí, según la PPT del cliente** ([C1-RF-58](06-requerimientos-preliminares.md)). Falta confirmar en qué inmuebles hay gas. |
| C1-Q-35 | ¿El rol de limpieza es semanal? ¿Cuánto se cobra por reemplazo y quién fija ese monto? |
| C1-Q-36 | ¿Qué gastos necesitan su aprobación? ¿Hay un monto mínimo? |

## Inmobiliario: valorización y rendimiento

| ID | Pregunta |
|----|----------|
| C1-Q-16 ⭐ | ¿El rendimiento se calcula sobre la **inversión** (costo + mejoras) o sobre el **valor actualizado** por UIT? ¿Qué impuestos y gastos se restan exactamente? |
| C1-Q-17 | ¿El ingreso se considera cuando se **cobra** o cuando **se debía cobrar**? |
| C1-Q-18 | ¿Las **mejoras** también se actualizan con la UIT desde el año en que se hicieron? |
| C1-Q-37 | ¿Qué tasa de referencia usamos para comparar (la de un plazo fijo que usted ingrese, por ejemplo 5.8 %)? |
| C1-Q-25 | ¿Está de acuerdo con los criterios y pesos propuestos para la calificación de inquilinos (puntualidad 50 %, atraso promedio 30 %, deuda 20 %)? |

## Roles y privilegios

| ID | Pregunta |
|----|----------|
| C1-Q-30 | ¿Los inquilinos deberían tener acceso al sistema en algún momento (para ver su deuda o subir vouchers), o solo reciben correos? |
| C1-Q-31 | ¿El analista puede **verificar** vouchers, o solo subirlos y la verificación la hace usted? |
| C1-Q-32 ⭐ | El analista necesita saber **cuánto cobrar** a cada inquilino. ¿Puede ver el monto individual de la cuota (pero no los totales, ganancias ni valores)? |

## Nuevas tras la última versión de los procesos

| ID | Pregunta |
|----|----------|
| C1-Q-39 | ¿Qué debe contener el **dossier de desalojo** y quién lo arma? ¿Hay un abogado que deba validarlo? |
| C1-Q-40 | ¿Cómo se define la **vacancia** para el Cap Rate? ¿Con qué alquiler de referencia? |
| C1-Q-41 | ¿Quién puede declarar una cuota como **incobrable**? ¿Se puede revertir si luego se paga? |

## Otras verticales (para el primer cliente de cada una)

| ID | Vertical | Pregunta |
|----|:--------:|----------|
| C1-Q-50 | 1.1 | ¿La comisión de administración se calcula sobre lo cobrado o sobre lo facturado? |
| C1-Q-51 | 1.1 | ¿La evaluación crediticia se hace con una central de riesgo externa? |
| C1-Q-52 | 1.2 | ¿Quién decide la alícuota y dónde consta? ¿La junta debe aprobar el presupuesto? |
| C1-Q-53 | 1.3 | ¿La garantía se bloquea en tarjeta (requiere pasarela) o se recibe como depósito? |
| C1-Q-54 | 1.3 | ¿Maquinaria y autos se tarifan igual? ¿Se alquila con operador? |
| C1-Q-55 | 1.4 | ¿Los créditos no usados se acumulan? ¿Se controla el acceso físico? |

> La definición del "monto" del tablero pasó a [NUC-Q-26](../../../general/01-analisis-negocio/08-preguntas-abiertas.md), porque afecta a todos los negocios.

## Tras la PPT del cliente

| ID | Pregunta |
|----|----------|
| C1-Q-56 ⭐ | En la reunión la alerta de atraso iba **directa al dueño**; en la PPT va "al analista y luego al gerente". ¿Confirmamos el escalamiento? ¿Con cuántos días cada nivel? |
| C1-Q-57 | ¿El autovalúo solo se archiva o también se registra su monto como gasto del inmueble? |