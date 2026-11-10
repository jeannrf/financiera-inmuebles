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

- Nombre, DNI, fecha de pago, monto a cobrar (alquiler).
- Tabla de servicios: departamento, número de suministro, lectura anterior, lectura actual, consumo, factor (por ejemplo, 0.87) y monto.
- Totales por departamento: agua, luz, mantenimiento y total a pagar.

> **Acción:** pedir al cliente sus Excel reales (anonimizados si lo prefiere) para validar campos. [PREGUNTA CLI-Q-02]

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
| Unidades en alquiler | **11** |
| Tipos de unidad | **Departamentos**, **alquiler en mercado** (puesto o local [INFERIDO → C1-Q-58]) y **cocheras** |
| Analistas al inicio | **1** |
| Negocios en el sistema | **2**: inmobiliario e inversiones financieras (sin tercer negocio por ahora) |
| Proyección a 2–3 años | Sin respuesta ([CLI-Q-11](02-preguntas-abiertas.md)) |
| Forma de entrega | Versión **web** [INFERIDO por su tamaño → NUC-Q-33] |

Falta saber cuántas unidades hay de cada tipo y en qué inmueble está cada una ([C1-Q-58](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/08-preguntas-abiertas.md)).

## 3.5 Parámetros confirmados

| Parámetro | Valor | Origen |
|-----------|-------|--------|
| Días de atraso para alertar al dueño | **7** | P7 |
| Canales de la alerta al dueño | Correo electrónico + bandeja del sistema | P7 |
| Pagos parciales | Permitidos | P8 |
| Interés o penalidad por mora | **Ninguno** | P8 |
| Método de prorrateo | **Proporcional al consumo** (método A), por suministro | P10 |
| Conceptos del recibo de agua | Agua + alcantarillado | P10 |
| Indicador del tablero inmobiliario | Ingresos efectivamente cobrados; meta: 100 % de ocupación | P6 |
