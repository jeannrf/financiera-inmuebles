# 08. Preguntas abiertas

> Las marcadas con ⭐ bloquean el diseño y conviene resolverlas primero. Las del piloto deben cerrarse antes del SRS.

## Inmobiliario: inmuebles, contratos y cobros

| ID | Pregunta |
|----|----------|
| C1-Q-10 | ¿El valor se registra por **edificio**, por **departamento** o por ambos? Si es por edificio, ¿cómo se reparte el rendimiento entre los departamentos? *(Parcial 11/Nov: con el método por m² de P11 el valor sale por unidad; falta confirmarlo.)* |
| C1-Q-11 | ¿Un contrato puede tener **varios inquilinos** (pareja, compañeros)? ¿Quién es el responsable del pago? |
| C1-Q-12 | ¿Qué medios de pago acepta (Yape, Plin, transferencia, efectivo)? ¿Hay depósito de garantía? ¿Cómo se registra y se devuelve? |
| ~~C1-Q-13~~ | ~~La alerta al dueño, ¿a los 5 o a los 7 días de atraso? ¿Quiere SMS, correo o ambos?~~ 🟢 **Respondida (10/Nov):** 7 días; correo + bandeja del sistema ([C1-RN-06](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-14 | ¿El saludo de cumpleaños se envía por correo? ¿Con algún texto o diseño en particular? |
| C1-Q-15 | ¿Se puede cerrar un mes si un inquilino quedó como **incobrable**? ¿Se puede **reabrir** un mes cerrado? *(Parcial 11/Nov: P12 confirma el incobrable a los 7 días; falta si se puede reabrir un mes.)* |
| ~~C1-Q-24~~ | ~~¿Se aceptan pagos parciales? ¿Se cobra mora o penalidad por atraso?~~ 🟢 **Respondida (10/Nov):** sí a pagos parciales; sin intereses ni penalidad ([C1-RN-39, C1-RN-40](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-28 | ¿El día de pago es el mismo para todos o depende de cada contrato? |
| C1-Q-29 | ¿Qué hacer con el contrato al renovarlo: se crea uno nuevo o se extiende el actual? ¿Con cuántos días de anticipación quiere la alerta? |

## Inmobiliario: servicios, mantenimiento y limpieza

| ID | Pregunta |
|----|----------|
| ~~C1-Q-19~~ | ~~Para el prorrateo, ¿porcentaje del consumo o factor (S/ por unidad)? ¿Cómo se reparte la diferencia?~~ 🟢 **Respondida (10/Nov):** proporcional al consumo, por suministro; la suma de submedidores es el total, así que no hay diferencia ([C1-RN-41, B3](05-reglas-de-negocio-y-calculos.md#b3-prorrateo-de-servicios-agua-y-luz)) |
| C1-Q-33 | ¿Qué conceptos se cobran como mantenimiento (vigilancia, ascensor, luz común, limpieza)? ¿Es un monto fijo o se reparte según los gastos del mes? |
| C1-Q-34 | ¿El gas también se prorratea? **Respondida: sí, según la PPT del cliente** ([C1-RF-58](06-requerimientos-preliminares.md)). Falta confirmar en qué inmuebles hay gas. |
| C1-Q-35 | ¿El rol de limpieza es semanal? ¿Cuánto se cobra por reemplazo y quién fija ese monto? |
| C1-Q-36 | ¿Qué gastos necesitan su aprobación? ¿Hay un monto mínimo? |

## Inmobiliario: valorización y rendimiento

| ID | Pregunta |
|----|----------|
| ~~C1-Q-16~~ | ~~¿Sobre la inversión o sobre el valor actualizado por UIT?~~ 🟢 **Respondida (11/Nov):** sobre el **valor de mercado por m² depreciado 1 % por año** ([B1-bis](05-reglas-de-negocio-y-calculos.md#b1-bis-rendimiento-de-mercado-por-metro-cuadrado-método-del-piloto)). La parte de impuestos pasa a C1-Q-63 |
| C1-Q-17 | ¿El ingreso se considera cuando se **cobra** o cuando **se debía cobrar**? *(En P11 el cliente usa el alquiler pactado por m²; falta saber si el rendimiento real usa lo cobrado.)* |
| C1-Q-18 | ¿Las **mejoras** también se actualizan con la UIT desde el año en que se hicieron? *(Sin respuesta; con el método por m² se reemplaza por C1-Q-65.)* |
| C1-Q-37 | ¿Qué tasa de referencia usamos para comparar (la de un plazo fijo que usted ingrese, por ejemplo 5.8 %)? |
| C1-Q-25 | ¿Está de acuerdo con los criterios y pesos propuestos para la calificación de inquilinos (puntualidad 50 %, atraso promedio 30 %, deuda 20 %)? |

## Roles y privilegios

| ID | Pregunta |
|----|----------|
| C1-Q-30 | ¿Los inquilinos deberían tener acceso al sistema en algún momento (para ver su deuda o subir vouchers), o solo reciben correos? |
| ~~C1-Q-31~~ | ~~¿El analista puede verificar vouchers?~~ 🟢 **Respondida (10/Nov):** sí, ve y verifica el comprobante |
| ~~C1-Q-32~~ | ~~¿Puede ver el monto individual de la cuota (pero no los totales)?~~ 🟢 **Respondida (10/Nov):** sí al monto individual; **nunca** la recaudación total ([matriz](03-actores-roles-privilegios.md#32-matriz-preliminar-de-privilegios), [NUC-RN-30](../../../general/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md)) |

## Nuevas tras la última versión de los procesos

| ID | Pregunta |
|----|----------|
| C1-Q-39 | ¿Qué debe contener el **dossier de desalojo** y quién lo arma? ¿Hay un abogado que deba validarlo? *(Sin respuesta en P12.)* |
| C1-Q-40 | ¿Cómo se define la **vacancia** para el Cap Rate? ¿Con qué alquiler de referencia? |
| C1-Q-41 | ¿Quién puede declarar una cuota como **incobrable**? ¿Se puede revertir si luego se paga? *(Parcial 11/Nov: cuándo → a los 7 días sin acuerdo de pago por partes. Falta quién y si se revierte; ver C1-Q-68.)* |

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
| C1-Q-56 ⭐ | En la reunión la alerta de atraso iba **directa al dueño**; en la PPT va "al analista y luego al gerente". ¿Confirmamos el escalamiento? ¿Con cuántos días cada nivel? *(Parcial 10/Nov: el nivel del dueño es 7 días; falta el del analista.)* |
| C1-Q-57 | ¿El autovalúo solo se archiva o también se registra su monto como gasto del inmueble? |
## Tras las respuestas al cuestionario (10/Nov/2026)

| ID | Pregunta |
|----|----------|
| C1-Q-58 ⭐ | "Alquiler de mercado": ¿es un **puesto o local dentro de un mercado**? ¿Cuántas unidades hay de cada tipo (departamentos, mercado, cocheras)? ¿Las cocheras y los puestos pagan servicios, mantenimiento o limpieza? ¿Tienen contrato igual que un departamento? |
| C1-Q-59 | La **meta mensual de cobranza** del tablero, ¿es la suma de los alquileres con **todas las unidades ocupadas** (propuesta) o un monto que usted fija? |
| C1-Q-60 | Si un inquilino abona una parte, ¿la alerta de 7 días se sigue contando desde el **vencimiento original**? (Propuesta: sí.) |
| C1-Q-61 | En el recibo de agua, ¿el **alcantarillado** y el **cargo fijo** se reparten junto con el agua según el consumo? |

## Tras las respuestas P11 y P12 (11/Nov/2026)

| ID | Pregunta |
|----|----------|
| C1-Q-62 ⭐ | Con el método por m², ¿se sigue usando la **UIT** para algo (valor patrimonial) o se deja de usar? ¿Le sirve ver también los años de recuperación sobre lo que invirtió? |
| C1-Q-63 ⭐ | El rendimiento por m², ¿es **bruto** o se restan impuestos (renta 5 %, predial, arbitrios) y mantenimiento no trasladado? |
| C1-Q-64 | ¿La depreciación de 1 % por año tiene un **tope** (por ejemplo, máximo 30 %)? ¿Es igual para cocheras y puestos de mercado? |
| C1-Q-65 | Si hace una **mejora** grande (pisos, remodelación), ¿cómo afecta al valor por m²: reduce la antigüedad, se suma aparte o no se considera? |
| C1-Q-66 | ¿Cada cuánto se actualiza el **estudio de mercado** (mensual, anual, antes de cada renovación)? ¿Qué fuentes usa el analista (portales, avisos)? |
| C1-Q-67 ⭐ | **Legal:** suspender agua y luz a un inquilino moroso puede tener consecuencias legales. ¿Lo ha validado con un abogado? ¿Está previsto en el contrato de alquiler? |
| C1-Q-68 ⭐ | A los 7 días sin acuerdo, ¿el sistema declara el incobrable **solo** o le **propone** al dueño y él confirma? (Propuesta: el dueño confirma.) |
| C1-Q-69 | Cuando el inquilino paga la deuda, ¿se **reponen** los servicios de inmediato? ¿Se cobra algún costo de reconexión? ¿La deuda deja de ser incobrable? |
