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
| ~~C1-Q-15~~ | ~~¿Se puede cerrar un mes con un incobrable? ¿Se puede reabrir?~~ 🟢 **Respondida (13/Nov):** sí se cierra; **solo se reabre si se cobró la deuda**; si no, queda cerrado y la deuda es incobrable no recuperable ([C1-RN-48](05-reglas-de-negocio-y-calculos.md)) |
| ~~C1-Q-24~~ | ~~¿Se aceptan pagos parciales? ¿Se cobra mora o penalidad por atraso?~~ 🟢 **Respondida (10/Nov):** sí a pagos parciales; sin intereses ni penalidad ([C1-RN-39, C1-RN-40](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-28 | ¿El día de pago es el mismo para todos o depende de cada contrato? ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** día de pago por contrato; si el mes no tiene ese día, vence el último día del mes. |
| C1-Q-29 | ¿Qué hacer con el contrato al renovarlo: se crea uno nuevo o se extiende el actual? ¿Con cuántos días de anticipación quiere la alerta? |

## Inmobiliario: servicios, mantenimiento y limpieza

| ID | Pregunta |
|----|----------|
| ~~C1-Q-19~~ | ~~Para el prorrateo, ¿porcentaje del consumo o factor (S/ por unidad)? ¿Cómo se reparte la diferencia?~~ 🟢 **Respondida (10/Nov):** proporcional al consumo, por suministro; la suma de submedidores es el total, así que no hay diferencia ([C1-RN-41, B3](05-reglas-de-negocio-y-calculos.md#b3-prorrateo-de-servicios-agua-y-luz)) |
| C1-Q-33 | ¿Qué conceptos se cobran como mantenimiento (vigilancia, ascensor, luz común, limpieza)? ¿Es un monto fijo o se reparte según los gastos del mes? |
| C1-Q-34 | ¿El gas también se prorratea? ~~Respondida: sí, según la PPT del cliente.~~ ⚙ **Default aplicado para SRS (24/Nov):** el Excel muestra que cada departamento con gas tiene **su propio suministro**, así que su costo se **traslada sin prorrateo** ([03-configuración, 3.2.3](../../../clientes/cliente-piloto/03-configuracion-y-datos.md#323-tabla-de-luz-y-gas-agua_luzjpg-parte-inferior)). Se confirma en la [ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md). |
| C1-Q-35 | ¿El rol de limpieza es semanal? ¿Cuánto se cobra por reemplazo y quién fija ese monto? |
| C1-Q-36 | ¿Qué gastos necesitan su aprobación? ¿Hay un monto mínimo? |

## Inmobiliario: valorización y rendimiento

| ID | Pregunta |
|----|----------|
| ~~C1-Q-16~~ | ~~¿Sobre la inversión o sobre el valor actualizado por UIT?~~ 🟢 **Respondida (11/Nov):** sobre el **valor de mercado por m² depreciado 1 % por año** ([B1-bis](05-reglas-de-negocio-y-calculos.md#b1-bis-rendimiento-de-mercado-por-metro-cuadrado-método-del-piloto)). La parte de impuestos pasa a C1-Q-63 |
| C1-Q-17 | ¿El ingreso se considera cuando se **cobra** o cuando **se debía cobrar**? *(En P11 el cliente usa el alquiler pactado por m²; falta saber si el rendimiento real usa lo cobrado.)* |
| C1-Q-18 | ¿Las **mejoras** también se actualizan con la UIT desde el año en que se hicieron? *(Sin respuesta; con el método por m² se reemplaza por C1-Q-65.)* |
| ~~C1-Q-37~~ | ~~¿Qué tasa de referencia usamos para comparar?~~ 🟢 **Respondida (13/Nov):** una **tasa media de plazo fijo que ingresa el analista** ([C1-RN-49](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-25 | ¿Está de acuerdo con los criterios y pesos propuestos para la calificación de inquilinos (puntualidad 50 %, atraso promedio 30 %, deuda 20 %)? |

## Roles y privilegios

| ID | Pregunta |
|----|----------|
| C1-Q-30 | ¿Los inquilinos deberían tener acceso al sistema en algún momento (para ver su deuda o subir vouchers), o solo reciben correos? *(Parcial 13/Nov: en el día a día el inquilino manda fotos y vouchers al analista, que los sube; el portal sigue en etapa 3.)* |
| ~~C1-Q-31~~ | ~~¿El analista puede verificar vouchers?~~ 🟢 **Respondida (10/Nov):** sí, ve y verifica el comprobante |
| ~~C1-Q-32~~ | ~~¿Puede ver el monto individual de la cuota (pero no los totales)?~~ 🟢 **Respondida (10/Nov):** sí al monto individual; **nunca** la recaudación total ([matriz](03-actores-roles-privilegios.md#32-matriz-preliminar-de-privilegios), [NUC-RN-30](../../../general/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md)) |

## Nuevas tras la última versión de los procesos

| ID | Pregunta |
|----|----------|
| ~~C1-Q-39~~ | ~~¿Qué debe contener el dossier de desalojo?~~ 🟢 **Respondida (13/Nov):** **no existe** en el sistema; el desalojo lo gestiona la empresa por fuera ([C1-RN-50](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-40 | ¿Cómo se define la **vacancia** para el Cap Rate? ¿Con qué alquiler de referencia? |
| ~~C1-Q-41~~ | ~~¿Quién declara el incobrable? ¿Se revierte si luego se paga?~~ 🟢 **Respondida (13/Nov):** lo **confirma el analista**; si se cobra, se reabre el mes para registrar el pago ([C1-RN-47, C1-RN-48](05-reglas-de-negocio-y-calculos.md)) |

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
| ~~C1-Q-56~~ | ~~¿Confirmamos el escalamiento? ¿Con cuántos días cada nivel?~~ 🟢 **Respondida (24/Nov):** la alerta al **analista** también es a los **7 días**, igual que al dueño ([C1-RN-38](05-reglas-de-negocio-y-calculos.md)) |
| C1-Q-57 | ¿El autovalúo solo se archiva o también se registra su monto como gasto del inmueble? |

## Tras las respuestas al cuestionario (10/Nov/2026)

| ID | Pregunta |
|----|----------|
| ~~C1-Q-58~~ | ~~"Alquiler de mercado": ¿qué es? ¿Cuántas unidades de cada tipo? ¿Qué pagan?~~ 🟢 **Respondida (24/Nov):** es un **puesto dentro de un mercado**. Hay **8 departamentos, 2 cocheras y 1 puesto**. Las cocheras tienen **contrato** de alquiler, pero **no** pagan limpieza ni mantenimiento. *(Lo que paga el puesto pasa a C1-Q-73.)* |
| C1-Q-59 | La **meta mensual de cobranza** del tablero, ¿es la suma de los alquileres con **todas las unidades ocupadas** (propuesta) o un monto que usted fija? ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** suma de los alquileres con todas las unidades ocupadas. |
| C1-Q-60 | Si un inquilino abona una parte, ¿la alerta de 7 días se sigue contando desde el **vencimiento original**? (Propuesta: sí.) ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** sí, desde el vencimiento original. |
| ~~C1-Q-61~~ | ~~¿El alcantarillado y el cargo fijo se reparten con el agua según el consumo?~~ 🟢 **Respondida por el Excel (24/Nov):** agua y alcantarillado se reparten **por separado**, ambos con el **% de consumo de agua**. El recibo solo trae esos dos montos ([3.2.2](../../../clientes/cliente-piloto/03-configuracion-y-datos.md#322-tabla-de-agua-agua_luzjpg-parte-superior)) |

## Tras las respuestas P11 y P12 (11/Nov/2026)

| ID | Pregunta |
|----|----------|
| ~~C1-Q-62~~ | ~~¿Se sigue usando la UIT?~~ 🟢 **Respondida (24/Nov):** la **UIT no se usa**. ⚙ **Default aplicado para SRS:** los años de recuperación sobre lo invertido se muestran como dato secundario, salvo que objete en la [ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md) |
| ~~C1-Q-63~~ | ~~¿Rendimiento bruto o neto?~~ 🟢 **Respondida (24/Nov):** **neto**: se restan los **impuestos** y el **mantenimiento** ([B1-bis](05-reglas-de-negocio-y-calculos.md#b1-bis-rendimiento-de-mercado-por-metro-cuadrado-método-del-piloto)) |
| C1-Q-64 | ¿La depreciación de 1 % por año tiene un **tope** (por ejemplo, máximo 30 %)? ¿Es igual para cocheras y puestos de mercado? ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** tope de 50 %, configurable. |
| C1-Q-65 | Si hace una **mejora** grande (pisos, remodelación), ¿cómo afecta al valor por m²: reduce la antigüedad, se suma aparte o no se considera? ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** no cambian el rendimiento por m²; se suman a la inversión para los años de recuperación. |
| C1-Q-66 | ¿Cada cuánto se actualiza el **estudio de mercado** (mensual, anual, antes de cada renovación)? ¿Qué fuentes usa el analista (portales, avisos)? |
| ~~C1-Q-67~~ | ~~**Legal:** ¿está validado el corte de agua y luz?~~ 🟢 **Respondida (24/Nov):** el cliente decide **cortar los servicios** sin más trámite. El equipo deja constancia del riesgo legal en el [registro de riesgos](05-reglas-de-negocio-y-calculos.md) (C1-RN-46) |
| ~~C1-Q-68~~ | ~~¿El sistema declara el incobrable solo o lo propone y alguien confirma?~~ 🟢 **Respondida (24/Nov, reemplaza la del 13/Nov):** el sistema lo **propone al dueño** y **el dueño decide** si es incobrable o no |
| C1-Q-69 | Cuando el inquilino paga la deuda, ¿se **reponen** los servicios de inmediato? ¿Se cobra algún costo de reconexión? *(Si se cobra, el mes se reabre para registrar el pago, C1-RN-48.)* ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** se reponen al cobrarse la deuda; sin costo de reconexión en el sistema. |

## Tras la conciliación de procesos (13/Nov/2026)

| ID | Pregunta |
|----|----------|
| C1-Q-70 | El analista recibe los pagos de servicios de los inquilinos. ¿Quién **paga el recibo al proveedor** (Sedapal, Enel, Luz del Sur): el analista con ese dinero o el dueño? ¿Se registra en el sistema? ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** paga el dueño; el analista registra el comprobante. |
| C1-Q-71 | ¿Quién **reabre** un mes cerrado cuando se cobra una deuda incobrable: el dueño o también el analista? (Propuesta: solo el dueño.) ⚙ **Default aplicado para SRS ([ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md)):** solo el dueño. |
| ~~C1-Q-72~~ | ~~Si el analista confirma el incobrable, ¿el dueño solo recibe aviso o lo aprueba?~~ 🟢 **Cerrada (24/Nov):** ya no aplica; el **dueño** decide el incobrable (C1-Q-68) |

## Ronda 2 y Excel del cliente (24/Nov/2026)

| ID | Pregunta |
|----|----------|
| C1-Q-73 ⭐ | El Excel de servicios tiene **9 departamentos** en un edificio (1A a 4B y 5.º piso), pero usted indicó **8**. ¿Cuál es el número correcto? ¿El puesto de mercado paga servicios o mantenimiento? |

> **Defaults aplicados para el SRS** (se envían en la [ronda 2](../../../clientes/cliente-piloto/05-cuestionario-ronda2-cierre.md); si el cliente no objeta, quedan aprobados):
> C1-Q-28 (fin de mes), C1-Q-34 (gas), C1-Q-59 (meta de cobranza), C1-Q-60 (alerta con pago parcial), C1-Q-64 (tope de depreciación),
> C1-Q-65 (mejoras), C1-Q-69 (reposición de servicios), C1-Q-70 (pago al proveedor) y C1-Q-71 (reapertura).
