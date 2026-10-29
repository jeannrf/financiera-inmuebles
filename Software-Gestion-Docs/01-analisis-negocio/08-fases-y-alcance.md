# 08. Propuesta de fases y alcance

> El cliente pidió explícitamente: "En la 1.ª etapa va a estar así, en la 2.ª así, en la 3.ª así, y
> esto acá no va a estar nunca". Esta es una **propuesta inicial** para discutir en el equipo y luego
> presentarla al cliente. Las duraciones son estimadas para unos 2 semestres.

## Criterios usados para dividir

1. Primero **lo que ahorra más tiempo y reduce más riesgo**: el control de cobros y las alertas de morosidad.
2. Cada etapa entrega algo **funcional de punta a punta** que el cliente puede usar con datos reales.
3. Lo que depende de terceros con costo o incertidumbre (WhatsApp, OCR, SMS masivo) va al final.

---

## Etapa 1: Núcleo + Cobranza inmobiliaria (unos 4 meses)

**Objetivo:** que el cliente deje de usar el Excel para los alquileres y reciba alertas automáticas.

- Usuarios, roles (Dueño / Analista) y privilegios.
- Inmuebles, departamentos, inquilinos (con DNI y datos laborales) y contratos.
- Cuotas mensuales automáticas, **historial de montos** e **incrementos programados**.
- Registro de pagos + **repositorio de vouchers** por período + verificación humana + aviso de archivo duplicado.
- **Alertas**: lista semanal y diaria para el analista, atraso ≥ 7 días para el dueño (**correo**), renovación de contrato.
- Historial del inquilino (estadías y atrasos).
- Importación inicial desde Excel y reportes básicos de cobranza.

**Entregable funcional:** el analista registra cobros y vouchers; el dueño recibe correos por morosidad y renovación.

## Etapa 2: Inmobiliario completo + Financiero + Tablero (unos 4–5 meses)

**Objetivo:** que el dueño vea **cuánto gana y cuánto vale** cada negocio.

- **Servicios**: recibos, lecturas con foto, **prorrateo** exacto y envío del resumen por correo.
- Mantenimiento con **aprobación de gastos** y **rol de limpieza**.
- **Mejoras**, **valorización por UIT** y **rendimiento** mensual y anual (comparado con un plazo fijo).
- **Calificación** de inquilinos (semáforo).
- **Cierre de mes** (candado).
- Saludo de cumpleaños.
- **Módulo financiero**: cuentas, plazos fijos (con alerta de vencimiento), operaciones de BVL, dividendos, rendimientos y **reporte tributario anual**.
- **Tablero multinegocio** con objetivos y semáforo, más **mensajería interna**.
- SMS para alertas críticas (si el presupuesto lo permite).

## Etapa 3: Integraciones y "lo deseado" (después de los 2 semestres o según el avance)

- Integración con **WhatsApp Business** (recibir vouchers y mensajes, enviar recordatorios).
- Chat o videollamada interna con los analistas.
- Lectura automática (OCR) de vouchers como sugerencia.
- Portal o app para el inquilino.
- Presupuestos de remodelación por m².
- Preparación como **producto multi-rubro** (plantillas para constructor, restaurante, cuentas por cobrar).

## Fuera de alcance (propuesta "no va a estar", salvo un nuevo acuerdo)

- Conexión directa con bancos o brókers y cotizaciones de bolsa en tiempo real.
- Declaración tributaria automática ante SUNAT (el sistema solo **calcula y reporta**).
- Que el sistema "decida" solo si un voucher es válido (siempre hay verificación humana).

---

## Recomendación técnica preliminar (para discutir en la arquitectura)

- **Aplicación web** (responsiva) en lugar de una app de escritorio: el cliente y los analistas acceden
  desde cualquier laptop o celular, hay una sola instalación, y aprovecha la experiencia del equipo en
  desarrollo web. [PREGUNTA P04]
- **Base de datos relacional (SQL)**, por ejemplo PostgreSQL o MySQL, ya que el dominio es muy relacional.
- **Tareas programadas** (cron o scheduler) para las cuotas y alertas, y un servicio de correo transaccional.
- **Almacenamiento de archivos** fuera de la base de datos (disco o almacenamiento de objetos), con acceso protegido.
- **Monolito modular**: un núcleo (negocios, usuarios, roles, documentos, alertas) y módulos (inmobiliario,
  financiero), lo que deja preparado el crecimiento a N negocios sin complicar el despliegue.

## Posible reparto del trabajo entre 3 personas (sugerido)

| Persona | Responsabilidad principal | Etapa 1 | Etapa 2 |
|---------|---------------------------|---------|---------|
| Integrante 1 | Núcleo y seguridad | Usuarios, roles, documentos, alertas y correo | Tablero, mensajería, cierre de mes |
| Integrante 2 | Inmobiliario | Inmuebles, inquilinos, contratos, cuotas, pagos | Servicios, prorrateo, limpieza, mantenimiento |
| Integrante 3 | Cálculos y finanzas | Historial, incrementos, reportes e importación de Excel | UIT, rendimiento, calificación, módulo financiero |
