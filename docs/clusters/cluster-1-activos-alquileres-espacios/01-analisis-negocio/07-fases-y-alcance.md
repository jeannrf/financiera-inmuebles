# 07. Fases y alcance

La hoja de ruta general está en [el documento general](../../../general/01-analisis-negocio/07-fases-y-alcance.md).

> El cliente pidió explícitamente: "En la 1.ª etapa va a estar así, en la 2.ª así, en la 3.ª así, y esto acá no va a estar nunca".

**Criterios:** primero lo que ahorra más tiempo y reduce más riesgo; cada etapa entrega algo funcional de punta a punta; lo que depende
de terceros con costo o incertidumbre (WhatsApp, OCR, SMS masivo) va al final.

## Etapa 1: Cobranza inmobiliaria (~4 meses)

**Objetivo:** que el cliente deje de usar el Excel para los alquileres y reciba alertas automáticas.

- Inmuebles (con año de construcción y zona), unidades alquilables por **tipo** (departamento, puesto de mercado, cochera, `C1-RF-60`) con **área en m²** (`C1-RF-65`), inquilinos (con DNI y datos laborales) y contratos.
- Cuotas mensuales automáticas, **historial de montos** e **incrementos programados**.
- Registro de pagos (incluidos **pagos parciales** sin intereses ni mora, `C1-RF-59`), **acuerdos de pago por partes** (`C1-RF-67`), **repositorio de vouchers** por período + verificación humana + aviso de archivo duplicado.
- Confirmación de cuotas **incobrables** a los 7 días sin acuerdo (`C1-RF-53`).
- **Alertas**: lista semanal y diaria para el analista (ocultando sumas y subtotales al analista, `C1-RF-63`), escalamiento por atraso (analista y luego dueño, por **correo**, [C1-RF-57](06-requerimientos-preliminares.md)), renovación de contrato.
- Historial del inquilino (estadías y atrasos).
- Importación inicial desde Excel y reportes básicos de cobranza.
- Guardar el **autovalúo** por año (C1-RF-55) y la **vista tipo tabla** de cuotas con columna de incremento (C1-RF-56).

**Entregable funcional:** el analista registra cobros y vouchers; el dueño recibe correos por morosidad y renovación.

## Etapa 2: Inmobiliario completo (~4–5 meses)

**Objetivo:** que el dueño vea **cuánto gana y cuánto vale** cada inmueble.

- **Servicios**: recibos por suministro (`C1-RF-61`), lecturas con foto, **prorrateo** proporcional exacto (agua y alcantarillado, y luz), traslado directo de **gas** por suministro propio (`C1-RF-58`), **registro de pagos de servicios** por el analista (`C1-RF-69`), suspensión/reposición de agua y luz (`C1-RF-68`) y envío del resumen por correo.
- Mantenimiento con **aprobación de gastos** y **rol de limpieza** (fotos subidas por el analista).
- **Mejoras**, **estudio de mercado por zona** (`C1-RF-64`), **alquiler sugerido** (`C1-RF-66`), **rendimiento neto mensual y anual por m²** (con depreciación 1 % anual; la UIT ya no se usa: `C1-Q-62`), comparación contra **tasa media de plazo fijo** ingresada por el analista (`C1-RF-54`), e indicador de **ocupación** en el tablero (`C1-RF-62`).
- **Calificación** de inquilinos (semáforo).
- **Cierre de mes** (candado), con reapertura solo si se cobra una deuda incobrable.
- Saludo de cumpleaños.

## Etapa 3: Integraciones y deseos

- Portal o app para el inquilino.
- Lectura automática (OCR) de vouchers como sugerencia, usando el servicio del núcleo.
- Recepción de vouchers por WhatsApp, usando el servicio del núcleo.

## Verticales 1.3 y 1.4 y extensión de 1.1 y 1.2

Se construyen **cuando haya un cliente real**. El contrato, el cobro, los documentos y las alertas ya estarán disponibles; faltarían las
piezas de [C1-RF-100 en adelante](06-requerimientos-preliminares.md#62-demás-verticales-inferido-a-partir-del-mapeo). Es el caso B del modelo comercial.

## Fuera de alcance

- Publicación automática en portales inmobiliarios.
- GPS o telemetría de flotas, y control físico de accesos (cerraduras, torniquetes).
- Tasación profesional del inmueble: se usa la aproximación del cliente (valor de mercado por m² depreciado).
- **Gestión de desalojos** y expedientes legales: la empresa los lleva fuera del sistema [CONFIRMADO — 13/Nov/2026].
