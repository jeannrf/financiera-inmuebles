# 03. Configuración y datos del cliente piloto

Esta información es lo que cargará su configuración del negocio (capa 5).

## 3.1 Sus zonas y modalidades

Hay inmuebles en al menos dos zonas, con modalidades distintas:

| Zona | Modalidad de servicios | Ejemplo mencionado |
|------|------------------------|--------------------|
| **San Martín de Porres** (edificio de unos 8 departamentos: 1A, 1B, 2A, 2B, 3B, 5.º piso…) | **El dueño paga** los recibos de agua y luz al proveedor y **cobra a cada inquilino** su parte según su consumo (prorrateo proporcional; cada departamento tiene medidor de agua y de luz, y algunos departamentos pueden estar en un suministro de luz distinto). Los inquilinos tienen un **rol de limpieza**. | Recibo de agua de S/ 300 repartido entre 8 departamentos |
| **Jesús María** (dpto. 501) | El inquilino **paga sus servicios directamente** o paga un paquete con todo incluido (limpieza y mantenimiento), unos **S/ 284–300** | Inquilino médico que prefiere pagar a limpiar |

> Motivo del cliente para pagar él mismo los servicios en algunos inmuebles: así evita que el
> inquilino retrase el pago y le corten el servicio a todo el edificio, o que deje una deuda al irse.

## 3.2 Información que hoy maneja en Excel (a migrar)

> **Insumos recibidos (24/Nov/2026)** [CONFIRMADO — Excel del cliente, `CLI-Q-02`]: capturas de sus Excel actuales.
> - `ejemplo.jpg`: la **tabla de inquilinos y cobro de alquiler**.
> - `agua_luz.jpg`: dos tablas de **servicios**, una para **agua** y otra para **luz** (con gas).
>
> Aquí se documenta **solo la estructura** (columnas y fórmulas). Los nombres, DNI y teléfonos de los inquilinos **no se copian**
> al repositorio (Ley 29733); las cifras de los ejemplos son totales del recibo, no datos personales.

### 3.2.1 Tabla de inquilinos y alquiler (`ejemplo.jpg`)

Una fila por unidad alquilada:

| Columna en el Excel | Contenido | Dónde va en el sistema |
|---------------------|-----------|------------------------|
| UBICACIÓN | Unidad, en texto libre ("SEGUNDO PISO A") | Unidad: código ("2A") + piso |
| NOMBRE | Nombre del inquilino | Inquilino |
| *(sin encabezado)* | **Teléfono** del inquilino | Inquilino: teléfono (la columna no tiene título) |
| FECHA PAGO | Día de pago en texto ("30 de cada Mes") | Contrato: día de pago (número 1–31) |
| MONTO A PAGAR | Alquiler mensual (S/) | Contrato: monto vigente con fecha de vigencia |
| DNI | Documento del inquilino | Inquilino: DNI |
| FIN DE CONTRATO | Fecha de fin del contrato | Contrato: fecha de fin (dispara la alerta de renovación) |
| Enero, Febrero, Marzo, PAGO Abril 2025, PAGO MAYO 2025… | **Una columna por mes** con el monto pagado | Cuotas y pagos: una cuota por período con su pago y voucher |

**Lo que cambia al pasar al sistema:**
- Las columnas por mes (con nombres que mezclan "Enero" sin año y "PAGO Abril 2025") pasan a ser **cuotas por período** con su estado. Es la vista tipo tabla de [C1-RF-56](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/06-requerimientos-preliminares.md).
- **Marcado de morosidad:** hoy, cuando un inquilino es moroso, se pinta de rojo **toda su fila** (todos sus datos). Esto se debe
  **ajustar**: el sistema marca solo la **cuota vencida** (su celda y su estado: *Vencida*, *Morosa*, *Incobrable*) y muestra el
  semáforo del inquilino aparte. Así se ve qué mes se debe sin perder la lectura del resto de los datos ([C1-RF-70](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/06-requerimientos-preliminares.md)).
- "30 de cada mes" no existe en febrero: hay que definir la regla de fin de mes ([C1-Q-28](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md)).

### 3.2.2 Tabla de agua (`agua_luz.jpg`, parte superior)

Título del período: *"PAGO DE AGUA (05 Septiembre al 05 Octubre)"*, rotulado como **OCTUBRE**. Una fila por departamento:

| Columna | Contenido |
|---------|-----------|
| INQUILINO | Nombre |
| DPTO | Unidad ("1 PISO A", "2 PISO B", "5 PISO") |
| Lectura INICIAL / Lectura Actual | Lecturas del medidor de agua del departamento, en m³ con **3 decimales** |
| Consumo (M3) | Lectura actual − lectura inicial |
| % DE CONSUMO | Consumo del departamento / consumo total |
| AGUA | Monto de agua del recibo × % de consumo |
| Alcantarillado | Monto de alcantarillado del recibo × % de consumo |
| COSTO DE AGUA | Agua + alcantarillado |

Bloque **MEDIDOR GENERAL**: monto total del recibo = agua + alcantarillado (en el ejemplo, S/ 282.30 = S/ 192.54 + S/ 89.76).

**Confirma** el método de [B3](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md#b3-prorrateo-de-servicios-agua-y-luz):
el agua y el **alcantarillado se reparten por separado, ambos con el % de consumo de agua** (responde [C1-Q-61](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md)).

> **Redondeo:** el Excel muestra los montos con 1 decimal. Si a cada inquilino se le cobra el monto mostrado, la suma da S/ 282.40,
> **10 céntimos más** que el recibo (S/ 282.30). Es justo el caso que corrige [C1-RN-10](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md):
> el sistema redondea a 2 decimales y ajusta el residuo para que la suma sea exacta.

### 3.2.3 Tabla de luz y gas (`agua_luz.jpg`, parte inferior)

Título: *"PAGO DE LUZ (05 Septiembre al 5 de Octubre)"*. Una fila por departamento:

| Columna | Contenido |
|---------|-----------|
| INQUILINO / DPTO | Nombre y unidad |
| SUMINISTRO ELECTRICO | Número de suministro del departamento (en el ejemplo hay **dos**: uno con 7 departamentos y otro con 2, resaltados en amarillo) |
| Lectura Anterior / Lectura Actual | Lecturas del medidor de luz, en kWh |
| Consumo (KW) | Lectura actual − lectura anterior |
| FACTOR DE CONSUMO | S/ por kWh **de su suministro** = monto del recibo / consumo total del suministro (0.87 y 0.84) |
| Costo Energía | Consumo × factor |
| Costo de Gas | Monto de gas del departamento (solo algunos) |
| Suministro de Gas | **Número de suministro de gas propio** de cada departamento que tiene gas |
| Costo Luz y Gas | Costo energía + costo de gas |

Pie de la tabla: un total por suministro eléctrico (recibo y consumo), el total de energía (S/ 524.00 = S/ 343.00 + S/ 181.00),
el total de gas (S/ 141.00), el total de luz y gas (S/ 665.00) y el **total de servicios del edificio** (S/ 947.30 = agua + luz + gas).

**Lo que confirma y lo que agrega:**
- **Confirma** el prorrateo **por suministro** de [C1-RN-41](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md):
  el factor de cada suministro es su recibo entre su consumo (343 / 394 ≈ 0.87; 181 / 214.76 ≈ 0.84), que equivale al reparto proporcional.
- El "factor 0.87" de la primera reunión es este factor por suministro, no una tarifa fija.
- **Gas: no se prorratea.** Cada departamento con gas tiene **su propio suministro**, y su costo se le **traslada tal cual** [INFERIDO del Excel → C1-Q-34].
  Esto corrige [C1-RF-58](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/06-requerimientos-preliminares.md), que suponía prorratear el gas como el agua y la luz.
- El período de lectura va **del día 5 al día 5** de cada mes.
- El edificio del Excel tiene **9 filas** (1A, 1B, 2A, 2B, 3A, 3B, 4A, 4B, 5.º piso), pero el cliente indicó **8 departamentos** en total [PREGUNTA C1-Q-73].

### 3.2.4 Póliza de la BVL

⏳ **Pendiente de recibir** ([INV-Q-27](../../modulos/inversiones-y-liquidez/01-analisis-negocio/08-preguntas-abiertas.md)). Sin ella, las
comisiones (SAB, BVL, CAVALI, SMV e IGV) quedan como **parámetros editables por operación**, según la propuesta del cuestionario (P13).

## 3.3 Datos de ejemplo de la reunión (referencia, no reales)

| Dato | Valor |
|------|-------|
| Valor de un inmueble | S/ 500 000 (comprado terminado); construyendo baja a unos S/ 300 000 |
| Alquiler | S/ 2 500 / mes |
| Impuestos anuales | unos S/ 2 000 |
| Mejora de pisos | S/ 50 000 |
| Mantenimiento | S/ 185 |
| Limpieza por reemplazo | S/ 40 |
| Paquete con todo incluido (Jesús María) | S/ 284–300 |
| Recibo de luz de un edificio | unos S/ 524 entre todos |
| Incremento de alquiler | S/ 2 000 → S/ 2 200 |

## 3.4 Dimensionamiento actual

Respuesta del 10 de noviembre de 2026 ([cuestionario, P5](04-cuestionario-validacion-reunion1.md#sección-3-respuestas-del-cliente-10-de-noviembre-de-2026)). [CONFIRMADO]

| Dato | Valor |
|------|-------|
| Unidades en alquiler | **11**: **8 departamentos**, **2 cocheras** y **1 puesto dentro de un mercado** [CONFIRMADO — 24/Nov, C1-Q-58] |
| Contrato por tipo | Las **cocheras** tienen contrato de alquiler, pero **no** pagan limpieza ni mantenimiento [CONFIRMADO — 24/Nov] |
| Analistas al inicio | **1** |
| Negocios en el sistema | **2**: inmobiliario e inversiones financieras (sin tercer negocio por ahora) |
| Proyección a 2–3 años | Sin respuesta ([CLI-Q-11](02-preguntas-abiertas.md)) |
| Forma de entrega | Versión **web**: el cliente la prefiere porque tiene pocos negocios. Para empresas más grandes habrá **versión de escritorio** [CONFIRMADO — 24/Nov, NUC-Q-33] |

Falta saber en qué inmueble está cada unidad y si el puesto de mercado paga servicios o mantenimiento; además, el Excel de
servicios muestra 9 departamentos en un solo edificio ([C1-Q-73](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md)).

## 3.5 Parámetros confirmados

| Parámetro | Valor | Origen |
|-----------|-------|--------|
| Días de atraso para alertar al dueño | **7** | P7 |
| Días de atraso para alertar al analista | **7** (igual que al dueño) | Ronda 2, C1-Q-56 |
| Canales de la alerta al dueño | Correo electrónico + bandeja del sistema | P7 |
| Pagos parciales | Permitidos | P8 |
| Interés o penalidad por mora | **Ninguno** | P8 |
| Método de prorrateo | **Proporcional al consumo** (método A), por suministro | P10 |
| Conceptos del recibo de agua | Agua + alcantarillado | P10 |
| Indicador del tablero inmobiliario | Ingresos efectivamente cobrados; meta: 100 % de ocupación | P6 |
| Base del rendimiento inmobiliario | Alquiler **neto** por m² (menos impuestos y mantenimiento) frente al precio de compra nuevo por m² de la zona, depreciado | P11 + ronda 2 (C1-Q-63) |
| UIT | **No se usa** para valorizar ni para el rendimiento | Ronda 2, C1-Q-62 |
| Depreciación por antigüedad | **1 % por año** | P11 |
| Quién hace el estudio de mercado | El analista; el dueño valida el precio por m² | P11 |
| Incobrable | A los **7 días** de atraso si no pidió pagar por partes. El sistema lo **propone al dueño** y él decide | P12 + ronda 2 (C1-Q-68) |
| Consecuencia del incobrable | Suspensión de agua y luz; el cliente decide aplicarla sin más validación | P12 + ronda 2 (C1-Q-67) |
| Período de lectura de medidores | Del día **5 al 5** de cada mes | Excel de servicios |
| Gas | Suministro propio por departamento; costo trasladado sin prorrateo [INFERIDO → C1-Q-34] | Excel de servicios |
| Despliegue | Servidores **operados por el equipo** para los clientes | Ronda 2, NUC-Q-32 |
| Anualización del rendimiento bursátil | Regla de tres (lineal), sumando utilidades | P13 |
| Monedas de las inversiones | Soles (S/) y dólares (US$) | P14 |
| Ganancia estimada de acciones no vendidas | **No** se muestra | P14 |
