# 07. Requerimientos preliminares

> Es un borrador para el SRS. La prioridad usa **MoSCoW**: **M** (Must, imprescindible), **S** (Should,
> importante), **C** (Could, deseable), **W** (Won't, por ahora no). La columna **Etapa** remite a `08-fases-y-alcance.md`.

## 7.1 Requerimientos funcionales

### Núcleo (transversal)

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| RF-01 | Iniciar sesión con usuario y contraseña | M | 1 |
| RF-02 | Gestionar usuarios y asignarles un rol (Dueño, Analista; N analistas) | M | 1 |
| RF-03 | Restringir pantallas y datos según el rol (el analista no ve montos agregados, ganancias ni valorizaciones) | M | 1 |
| RF-04 | Gestionar **negocios** (N), cada uno con un objetivo mensual | S | 2 |
| RF-05 | **Tablero** de inicio con una tarjeta por negocio: monto real frente al objetivo, semáforo y acceso al módulo | S | 2 |
| RF-06 | **Mensajería interna** analista → dueño (por ejemplo, gasto pendiente de aprobación), marcable como leída | S | 2 |
| RF-07 | Bandeja de **alertas** dentro del sistema | M | 1 |
| RF-08 | Enviar alertas por **correo electrónico** | M | 1 |
| RF-09 | Enviar alertas por **SMS** | C | 2–3 |
| RF-10 | Repositorio de **documentos** (imágenes o PDF) asociados a entidades, consultables por período | M | 1 |
| RF-11 | Configurar parámetros: días de umbral de alerta, tasas de impuestos, tabla de UIT, tasa de referencia | M | 1–2 |
| RF-12 | Bitácora de auditoría (quién registró o cambió qué y cuándo) | S | 1 |

### Inmobiliario

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| RF-20 | Registrar inmuebles (dirección, valor base, año base, suministros, modalidad de servicios) | M | 1 |
| RF-21 | Registrar departamentos con código libre, piso y submedidores | M | 1 |
| RF-22 | Registrar inquilinos: nombre, DNI, teléfono, correo, fecha de nacimiento, datos laborales | M | 1 |
| RF-23 | Adjuntar al inquilino la copia del DNI y la boleta de pago | M | 1 |
| RF-24 | Registrar contratos (inquilino, departamento, fechas, día de pago, monto, conceptos) | M | 1 |
| RF-25 | Generar automáticamente las **cuotas mensuales** de cada contrato | M | 1 |
| RF-26 | Mantener el **historial de montos** por contrato (no editar ni borrar; nueva fila con vigencia) | M | 1 |
| RF-27 | **Programar incrementos** de alquiler con fecha futura | M | 1 |
| RF-28 | Registrar pagos y **subir el voucher**, asociado a inquilino, departamento, período y concepto | M | 1 |
| RF-29 | **Verificar** el voucher (confirmación humana) y marcar la cuota como pagada | M | 1 |
| RF-30 | Advertir si se sube un **archivo idéntico** a uno ya existente (comparando hash) | S | 1 |
| RF-31 | Consultar los vouchers por inquilino y período ("muéstrame todos los vouchers de 2026") | M | 1 |
| RF-32 | Lista **semanal** de cobros y lista de "hoy vence" para el analista | M | 1 |
| RF-33 | Alerta al dueño por atraso ≥ N días (configurable, 7 por defecto) | M | 1 |
| RF-34 | Alerta de **renovación de contrato** X días antes de su vencimiento | M | 1 |
| RF-35 | Historial del inquilino: estadías, atrasos y deudas (incluye inquilinos que regresan) | M | 1 |
| RF-36 | **Calificación** del inquilino (verde, amarillo o rojo) con criterios ponderados configurables | S | 2 |
| RF-37 | Registrar recibos de agua y luz del proveedor (uno o más suministros) con su archivo | M | 2 |
| RF-38 | Registrar lecturas de submedidores con foto; la lectura anterior se toma del mes previo | M | 2 |
| RF-39 | **Calcular el prorrateo** por departamento con cuadre exacto al total del recibo | M | 2 |
| RF-40 | Generar el **resumen de servicios** por inquilino y enviarlo por correo con los adjuntos | S | 2 |
| RF-41 | Registrar si el dueño ya pagó el recibo al proveedor | S | 2 |
| RF-42 | Registrar gastos de mantenimiento con el flujo **solicitud → aprobación del dueño** | S | 2 |
| RF-43 | **Rol de limpieza**: cronograma, evidencia fotográfica, estados y cargo por reemplazo | S | 2 |
| RF-44 | Registrar **mejoras** que se suman al costo del inmueble | M | 2 |
| RF-45 | Calcular el **valor actualizado** del inmueble con la UIT (más mejoras) | M | 2 |
| RF-46 | Calcular el **rendimiento** mensual y anual, los años de recuperación y la comparación con un plazo fijo, por inmueble y total | M | 2 |
| RF-47 | **Cierre de mes** con validaciones (sin deudas, vouchers completos, servicios pagados) y bloqueo de cambios | S | 2 |
| RF-48 | Saludo automático de **cumpleaños** por correo | C | 2 |
| RF-49 | Exportar reportes (cobranza, morosidad, rendimiento) a Excel o PDF | S | 2 |
| RF-50 | Importar los datos iniciales desde los Excel actuales del cliente | S | 1 |

### Financiero

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| RF-60 | Registrar cuentas bancarias (entidad, moneda, saldo, TEA) | M | 2 |
| RF-61 | Registrar plazos fijos (monto, TEA, apertura, vencimiento) y calcular el interés esperado | M | 2 |
| RF-62 | Alerta de vencimiento de plazo fijo | S | 2 |
| RF-63 | Registrar operaciones de bolsa (compra y venta, cantidad, precio, comisiones, impuestos) | M | 2 |
| RF-64 | Registrar dividendos o utilidades recibidos | S | 2 |
| RF-65 | Calcular la ganancia o pérdida y el rendimiento % por operación, por acción y total | M | 2 |
| RF-66 | Resumen financiero: total por tipo de instrumento, rendimiento ponderado y ranking | M | 2 |
| RF-67 | **Reporte anual** de ganancias de capital para el impuesto a la renta | M | 2 |

### Etapa 3 / deseos (fuera del alcance de las etapas 1-2)

| ID | Requerimiento | Prioridad | Etapa |
|----|---------------|:---------:|:-----:|
| RF-80 | Integración con **WhatsApp** (recibir mensajes y vouchers dentro del software, enviar recordatorios) | C | 3 |
| RF-81 | Chat o **videollamada** interna con el analista | C | 3 |
| RF-82 | Lectura automática de vouchers (OCR) para sugerir monto y fecha | C | 3 |
| RF-83 | Portal o app para el inquilino (ver su deuda, subir vouchers, reportar limpieza) | C | 3 |
| RF-84 | **Presupuestos de remodelación** por m² (material + mano de obra) | C | 3 |
| RF-85 | Plantillas para **otros rubros** (constructor, restaurante, cuentas por cobrar) | W | Futuro |
| RF-86 | Importación automática desde bancos o brókers y precios de bolsa en línea | W | Futuro |

## 7.2 Requerimientos no funcionales

| ID | Categoría | Requerimiento |
|----|-----------|---------------|
| RNF-01 | **Seguridad** | Contraseñas con hash (bcrypt o Argon2); sesiones con expiración; control de acceso por rol aplicado en el **servidor**, no solo en la interfaz |
| RNF-02 | **Privacidad** | Se guardan datos personales (DNI, copias del DNI, datos laborales, boletas): hay que cumplir la **Ley 29733** de Protección de Datos Personales (consentimiento del inquilino, acceso restringido, archivos no públicos) |
| RNF-03 | **Integridad** | Los registros históricos son inmutables (RN-01) y los períodos cerrados se bloquean; queda auditoría de los cambios |
| RNF-04 | **Disponibilidad y respaldo** | Copias de seguridad automáticas diarias de la base de datos y de los archivos; procedimiento de restauración probado |
| RNF-05 | **Escalabilidad** | Arquitectura modular: un núcleo común más módulos por negocio; agregar un negocio o rubro no debe requerir rehacer el núcleo. Debe soportar cientos de departamentos sin degradarse |
| RNF-06 | **Usabilidad** | Interfaz interactiva y sencilla para un usuario no técnico; las tareas frecuentes (registrar pago y voucher) en ≤ 3 pasos; en español; moneda S/ con formato peruano |
| RNF-07 | **Portabilidad** | Accesible desde una laptop (navegador) y usable en el celular (diseño responsivo) [ver P04] |
| RNF-08 | **Rendimiento** | Las pantallas principales cargan en < 2 s con los volúmenes esperados |
| RNF-09 | **Confiabilidad de alertas** | Las tareas programadas (cuotas, alertas) se ejecutan a diario aunque nadie abra el sistema; los envíos fallidos se reintentan y se registran |
| RNF-10 | **Precisión** | Los cálculos monetarios usan tipo decimal (nunca coma flotante) y un redondeo definido |
| RNF-11 | **Mantenibilidad** | Código versionado (Git), pruebas automáticas de los cálculos críticos y documentación |
| RNF-12 | **Configurabilidad** | Las tasas de impuestos, la UIT, los umbrales y los pesos de la calificación son parámetros, no valores fijos en el código |
| RNF-13 | **Almacenamiento** | Soporta imágenes y PDF de hasta ~10 MB, organizados por inmueble, inquilino y período |

## 7.3 Restricciones conocidas

- El equipo tiene experiencia en **desarrollo web** y **SQL**; plazo de unos **2 semestres**, con 3 personas que trabajan los domingos y en su tiempo libre.
- Presupuesto bajo para servicios de pago: hay que elegir proveedores de correo, SMS y hosting con planes gratuitos o baratos.
- La integración con WhatsApp tiene costo y requisitos (API oficial de WhatsApp Business), por eso se deja para la etapa 3.
