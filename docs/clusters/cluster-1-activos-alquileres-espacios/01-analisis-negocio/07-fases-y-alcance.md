# 07. Fases y alcance

La hoja de ruta general está en [el documento general](../../../general/01-analisis-negocio/07-fases-y-alcance.md).

> El cliente pidió explícitamente: "En la 1.ª etapa va a estar así, en la 2.ª así, en la 3.ª así, y esto acá no va a estar nunca".

**Criterios:** primero lo que ahorra más tiempo y reduce más riesgo; cada etapa entrega algo funcional de punta a punta; lo que depende
de terceros con costo o incertidumbre (WhatsApp, OCR, SMS masivo) va al final.

## Etapa 1: Cobranza inmobiliaria (~4 meses)

**Objetivo:** que el cliente deje de usar el Excel para los alquileres y reciba alertas automáticas.

- Inmuebles, departamentos, inquilinos (con DNI y datos laborales) y contratos.
- Cuotas mensuales automáticas, **historial de montos** e **incrementos programados**.
- Registro de pagos + **repositorio de vouchers** por período + verificación humana + aviso de archivo duplicado.
- **Alertas**: lista semanal y diaria para el analista, atraso ≥ 7 días para el dueño (**correo**), renovación de contrato.
- Historial del inquilino (estadías y atrasos).
- Importación inicial desde Excel y reportes básicos de cobranza.

**Entregable funcional:** el analista registra cobros y vouchers; el dueño recibe correos por morosidad y renovación.

## Etapa 2: Inmobiliario completo (~4–5 meses)

**Objetivo:** que el dueño vea **cuánto gana y cuánto vale** cada inmueble.

- **Servicios**: recibos, lecturas con foto, **prorrateo** exacto y envío del resumen por correo.
- Mantenimiento con **aprobación de gastos** y **rol de limpieza**.
- **Mejoras**, **valorización por UIT** y **rendimiento** mensual y anual.
- **Calificación** de inquilinos (semáforo).
- **Cierre de mes** (candado) y dossier de desalojo.
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
- Tasación profesional del inmueble: la UIT es una aproximación elegida por el cliente.
