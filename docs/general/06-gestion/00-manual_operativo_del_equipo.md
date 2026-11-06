# Manual Operativo de Ingeniería — Equipo Core SaaS (John, Jeanpier, Ilia)

> **Propósito:** Definir las reglas de juego, el flujo diario en **Linear**, el estándar de ramas/commits en **Git** y el método de trabajo asistido por IA en **Antigravity** para entregar con estándar corporativo la **Fase 0 (28 de noviembre de 2026)** y las etapas de código posteriores.

## 1. Roles Oficiales del Equipo

Aunque los tres somos ingenieros full-stack y revisamos el trabajo de todos, cada uno es **Dueño de Dominio (Owner)** de un área específica para no pisarnos el trabajo:

| Integrante | Rol Principal | Responsabilidad en Fase 0 (06 Nov – 28 Nov) | Responsabilidad en Desarrollo (Etapas 1 y 2) |
|------------|---------------|---------------------------------------------|--------------------------------------------|
| **John** | **TPM & Arquitecto Core SaaS** | Contacto con Cliente Piloto, Acuerdo Comercial/PI, SRS del Núcleo (`NUC`), Arquitectura C4/ADRs y Cronograma Gantt (`FIN-01, 02, 04, 09, 13, 16`). | Capa 1 (Núcleo Multi-tenant, RBAC, Seguridad, Alertas Cron, Tablero *Holding View*, Cierre de Mes). |
| **Jeanpier** | **Líder Dominio Clúster 1 & UX/UI** | SRS Clúster 1 Inmobiliario (`C1`), Diseño de Wireframes (Core y C1) y Armado del Deck PowerPoint (`FIN-05, 10, 11, 15`). | Paquete Clúster 1 (Inmuebles, Dptos, Contratos, Vouchers, Prorrateo Agua/Luz, Limpieza) y Frontend UX. |
| **Ilia** | **Líder Motor Financiero, Datos & QA** | Conciliación de Fórmulas, SRS Inversiones (`INV`), Modelo ERD Completo (Core + C1 + INV), UX Inversiones y Trazabilidad (`FIN-03, 06, 07, 08, 12, 14`). | Esquema SQL PostgreSQL (RLS), Motor de Cálculos (`DECIMAL`), Valorización UIT, Cap Rate y Módulo Inversiones (BVL/Plazos Fijos). |

## 2. Cómo Trabajamos en Linear Día a Día

Linear es nuestra única fuente de verdad para saber **quién está haciendo qué y para cuándo**.

### 2.1 Estados de una Issue (Workflow)
Cada tarea (`FIN-XX`) pasa obligatoriamente por estos 4 estados:
1. **`Todo`:** Tarea planificada en el Ciclo semanal actual, aún no iniciada.
2. **`In Progress`:** La persona asignada ya está trabajando activamente en ella. *(Regla: Nadie debe tener más de 2 tareas en `In Progress` al mismo tiempo).*
3. **`In Review` (o comentario de revisión):** El archivo `.md` o código ya se subió a Git y requiere una leída rápida de los otros dos compañeros.
4. **`Done`:** Todos los **Criterios de Aceptación** de la issue se cumplieron y los archivos están en la rama principal del repositorio.

### 2.2 Nuestro Ritmo Semanal (Ciclos)
* **Ciclo 1 (06 Nov – 12 Nov):** Cerrar preguntas con el cliente, firmar acuerdo interno de equipo y conciliar fórmulas (`FIN-01`, `FIN-02`, `FIN-03`).
* **Ciclo 2 (13 Nov – 20 Nov):** Redactar los 3 SRS (`NUC`, `C1`, `INV`), diseñar el ERD del Núcleo y bocetar el Tablero *Holding View* (`FIN-04`, `FIN-05`, `FIN-06`, `FIN-07`, `FIN-10`).
* **Ciclo 3 (21 Nov – 27 Nov):** Cerrar ERD de verticales, Arquitectura C4, Wireframes de C1 e Inversiones, Cronograma Gantt, Presentación PowerPoint y Simulacro (`FIN-08`, `FIN-09`, `FIN-11`, `FIN-12`, `FIN-13`, `FIN-14`, `FIN-15`, `FIN-16`).
* **Reunión de Sincronización (Domingos):** Revisión rápida de 20 minutos mirando la vista **Active Cycle** en Linear para destrabar bloqueos.

## 3. Estándar de Git y Vinculación con Linear

Para mantener el repositorio limpio y profesional, vincularemos cada cambio con el código de la issue de Linear (`FIN-XX`) utilizando mensajes de commit en **inglés**:

### 3.1 Ramas (Branches)
Cuando pases una tarea a `In Progress`, crea una rama con el ID de Linear:
```bash
git checkout -b docs/FIN-01-questionnaire-client
```

### 3.2 Mensajes de Commit (Conventional Commits en Inglés)
Siempre incluye el código de la issue en el mensaje:
```bash
git add .
git commit -m "docs(FIN-01): generate executive validation questionnaire for pilot client"
git push origin docs/FIN-01-questionnaire-client
```

## 4. Flujo de Trabajo con Agentes de IA en Antigravity

No redactamos documentos extensos ni código repetitivo desde cero: actuamos como **Arquitectos y Revisores** sobre el agente de Antigravity.

**Los 4 pasos para completar cualquier Issue en Antigravity:**
1. **Leer la Issue en Linear:** Revisa los *Entregables en el repositorio* y los *Criterios de Aceptación* de tu tarea `FIN-XX`.
2. **Lanzar el Prompt Contextualizado:** Pídele al agente de Antigravity que lea primero `resumen_estrategico_saas_fase0.md` y los archivos de `01-analisis-negocio/` correspondientes antes de generar el entregable.
3. **Auditar las Reglas de Oro:** Antes de dar por bueno lo que generó la IA, verifica que:
   * No mezcle vocabulario inmobiliario dentro de `docs/general/` (el Núcleo es 100% agnóstico).
   * Respete la inmutabilidad (`NUC-RN-01`: nada se borra, todo usa vigencia histórica).
   * Respete el ocultamiento de ganancias para analistas (`NUC-RN-12`).
   * Toda tabla tenga `organizacion_id` y `negocio_id`.
4. **Guardar, Subir a Git y Marcar `Done` en Linear.**

## 5. Plan de Acción Inmediato: Qué hace cada uno esta Semana (Ciclo 1: 06 Nov – 12 Nov)

### 👤 Paso 1 para JOHN (Hoy, Viernes 6 – Lunes 9 Nov)
1. Mover **`FIN-01`** a **`In Progress`** en Linear.
2. Ejecutar en Antigravity el prompt de generación de `docs/clientes/cliente-piloto/04-cuestionario-validacion-reunion1.md`.
3. Revisar el mensaje junto a Jeanpier e Ilia y enviárselo al Cliente Piloto por WhatsApp/Correo solicitando sus Excel actuales y confirmando las preguntas críticas.
4. Iniciar **`FIN-02`** (vence el 11 Nov): generar `docs/general/06-gestion/01-acuerdo-equipo-y-modelo-comercial.md` para dejar firmado nuestro acuerdo interno de Propiedad Intelectual (Opción A: Plataforma SaaS del equipo + Cliente Fundador).

### 👤 Paso 1 para ILIA y JEANPIER (Este Fin de Semana – Jueves 12 Nov)
1. Mover **`FIN-03`** a **`In Progress`** en Linear.
2. Conciliar los 9 puntos pendientes en `docs/clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/04-procesos-de-negocio.md` y cerrar las fórmulas duales de Cap Rate / UIT y tributación BVL en `05-reglas-de-negocio-y-calculos.md`.
3. Dejar el terreno listo para que el viernes 13 de noviembre arranquemos el **Ciclo 2** con los tres SRS (`FIN-04` John, `FIN-05` Jeanpier, `FIN-06` Ilia).

## 6. Prompts Listos para Ejecutar el Ciclo 1 Completo (`FIN-01`, `FIN-02`, `FIN-03`)

### Prompt para `FIN-01` (John)
```markdown
Actúa como un Product Manager Senior. Vamos a ejecutar la issue `FIN-01` definida en `resumen_estrategico_saas_fase0.md`.
Lee `resumen_estrategico_saas_fase0.md` (§3.2 y §4.1) y todos los archivos de `docs/clientes/cliente-piloto/`.
Genera `docs/clientes/cliente-piloto/04-cuestionario-validacion-reunion1.md` con:
1) Un mensaje ejecutivo corto listo para enviar por WhatsApp/Correo al cliente pidiendo sus Excel actuales (alquileres y agua/luz), un ejemplo de voucher y una póliza BVL, y confirmando la fecha del coworking (~28 nov).
2) El pliego de las 14 preguntas bloqueantes redactadas en lenguaje de negocios claro, incluyendo en cada una la "Propuesta recomendada por el equipo" para que pueda aprobarlas rápidamente.
Actualiza también `docs/clientes/cliente-piloto/02-preguntas-abiertas.md` referenciando este archivo.
```

### Prompt para `FIN-02` (John)
```markdown
Actúa como un Consultor Legal Tecnológico y Estratega SaaS B2B. Vamos a ejecutar la issue `FIN-02` definida en `resumen_estrategico_saas_fase0.md`.
Lee `resumen_estrategico_saas_fase0.md` (`FIN-02`), `docs/general/01-analisis-negocio/01-vision-y-modelo-de-negocio.md` y `docs/general/01-analisis-negocio/08-preguntas-abiertas.md`.
Genera el archivo `docs/general/06-gestion/01-acuerdo-equipo-y-modelo-comercial.md` con:
1) Acuerdo Interno del Equipo Fundador (John, Jeanpier, Ilia): participación equitativa, titularidad del código base como activo de la futura empresa del equipo, reglas de confidencialidad y toma de decisiones.
2) Propuesta de Modelo Comercial para el Cliente Piloto (Opción A): por qué el modelo SaaS Web le beneficia en costos de mantenimiento y evolución, y qué beneficios exclusivos recibe como "Cliente Fundador / Piloto" (tarifa preferencial en Etapas 1 y 2, prioridad para su 3.er negocio y membresía bonificada).
3) Política comercial para nuevos clientes según los Casos A, B, C y D de la fábrica de software.
```

### Prompt para `FIN-03` (Ilia & Jeanpier)
```markdown
Actúa como un Analista Funcional Senior y Especialista en Finanzas Inmobiliarias/Bursátiles. Vamos a ejecutar la issue `FIN-03` definida en `resumen_estrategico_saas_fase0.md`.
Lee `resumen_estrategico_saas_fase0.md` (`FIN-03` y §4.2), `docs/clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/04-procesos-de-negocio.md`, `05-reglas-de-negocio-y-calculos.md` y `docs/modulos/inversiones-y-liquidez/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md`.
Realiza las siguientes actualizaciones:
1) En `C1/04-procesos-de-negocio.md`: resuelve e integra en el flujo principal los 9 puntos de la tabla §4.2 (paso de pago al proveedor de servicios C1-RF-41, carga de fotos de limpieza por el analista en Etapas 1-2, estados completos del rol de limpieza y contenido del Dossier de Desalojo C1-RF-51), marcando la tabla de brechas como conciliada.
2) En `C1/05-reglas-de-negocio-y-calculos.md`: formaliza las fórmulas duales de rentabilidad (ROI sobre Inversión Histórica + Mejoras vs. Cap Rate sobre Valor Actualizado UIT; e Ingreso Cobrado/Caja vs. Proyectado con tasa de vacancia) y la tabla de parámetros configurables.
3) En `INV/05-reglas-de-negocio-y-calculos.md`: estandariza las fórmulas de costos reales BVL (comisión SAB, BVL, CAVALI, SMV, IGV 18%) y el cálculo parametrizable del Impuesto a la Renta de 2.ª Categoría (5% con tramo de exoneración en UIT).
```