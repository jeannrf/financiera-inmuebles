# 10. Mapa de clústeres y reutilización

## 10.1 Los 6 clústeres

| # | Clúster | Qué vende | Entidad principal | Verticales | Forma de cobro típica |
|---|---------|-----------|-------------------|------------|-----------------------|
| [1](../../clusters/cluster-1-activos-alquileres-espacios/README.md) | Activos, Alquileres y Espacios | Uso temporal de un bien | Activo / Unidad | 1.1 Inmobiliarias · 1.2 Edificios y condominios · 1.3 Rent-a-car y flotas · 1.4 Coworking y self-storage | Recurrente |
| [2](../../clusters/cluster-2-comercial-alto-valor/README.md) | Comercial de Alto Valor | Cierres consultivos de ticket alto | Oportunidad / Expediente | 2.1 Seguros · 2.2 Concesionarias · 2.3 Instalaciones técnicas · 2.4 Viajes | Cuotas, hitos, comisiones |
| [3](../../clusters/cluster-3-servicios-profesionales-proyectos/README.md) | Servicios Profesionales por Proyectos | Conocimiento, tiempo, entregables | Proyecto / Expediente | 3.1 Contables y legales · 3.2 Marketing y software · 3.3 Arquitectura y construcción · 3.4 RR. HH. | Iguala, hitos, certificación |
| [4](../../clusters/cluster-4-citas-agendas-suscripciones/README.md) | Citas, Agendas y Suscripciones | Bloques de tiempo a personas | Persona atendida + Agenda | 4.1 Clínicas · 4.2 Academias · 4.3 Gimnasios · 4.4 Veterinarias | Paquetes, membresías, caja diaria |
| [5](../../clusters/cluster-5-servicio-tecnico-campo/README.md) | Servicio Técnico en Campo | Reparar o mantener un bien del cliente | Orden de Trabajo | 5.1 Talleres · 5.2 Electrónica y TI · 5.3 Mantenimiento y limpieza | Por OT, abonos |
| [6](../../clusters/cluster-6-comercio-distribucion-produccion/README.md) | Comercio, Distribución y Producción | Bienes físicos | Pedido + Producto (SKU) | 6.1 Mayoristas · 6.2 A medida · 6.3 Minorista y restaurantes [EQUIPO] | Contado, crédito, anticipos |

**Fuera de los clústeres:** [Inversiones y Liquidez](../../modulos/inversiones-y-liquidez/README.md), módulo complementario ([decisión NUC-Q-01](08-preguntas-abiertas.md#decisiones-tomadas)).

## 10.2 Cómo clasificar un negocio nuevo

Se usa en NUC-P-16 y sirve de guía al asistente IA. Se responde en orden y gana la primera coincidencia:

```
¿Qué le compra realmente el cliente?
│
├─ El USO TEMPORAL de un bien del negocio ................................ C1
├─ Un BIEN FÍSICO que sale de stock o se fabrica ......................... C6
├─ La REPARACIÓN o el MANTENIMIENTO de un bien que ya es del cliente ..... C5
├─ UN BLOQUE DE TIEMPO, un paquete o membresía, con agenda o cupo ........ C4
├─ Un ENTREGABLE o CONOCIMIENTO por proyecto o iguala .................... C3
└─ Un CIERRE de ticket alto, con cotización negociada y comisión ......... C2
```

**Casos de frontera** [INFERIDO]:

| Negocio | Va en | Por qué |
|---------|-------|---------|
| Instaladora solar | C2 (2.3), al pasar a mantenimiento usa C5 | Lo difícil es vender y presupuestar |
| Empresa de limpieza de edificios | C5 (5.3) | Le da servicio al edificio; 1.2 lo administra |
| Peluquería, spa | C4 | Vende turnos, aunque venda productos |
| Ferretería | Mayorista: C6.1 · Tienda: C6.3 | Sus procesos cambian con el crédito y el volumen |
| Restaurante | C6.3 | Vende mucho y controla insumos; agrega mesas y recetas |
| Constructora con venta de departamentos | C3 (3.3) para la obra; C2 para la venta | Son dos negocios dentro de la misma organización |
| Dueño que alquila y gestiona edificio propio | C1 (1.1 + 1.2) | Es el caso del cliente piloto |

**Regla de desempate:** si un negocio cae en dos clústeres, se modela como **dos negocios** en la misma organización,
y no se mezclan paquetes en uno solo.

## 10.3 Matriz de reutilización

Tomada del documento de mapeo:

| Módulo del Motor Base | Clúster 1 (Activos) | Clúster 2 (Comercial) | Clúster 3 (Proyectos) | Clúster 4 (Citas/B2C) | Clúster 5 (Técnico) | Clúster 6 (Comercio) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Finanzas, Caja y P&L** | Crítico | Crítico | Crítico | Crítico | Crítico | Crítico |
| **CRM y Pipelines (Kanban)** | Alto | Crítico | Alto | Bajo | Medio | Medio |
| **Contratos y Cobro Recurrente** | Crítico | Medio | Alto | Alto | Medio | Bajo |
| **Agenda, Turnos y Calendario** | Medio | Medio | Bajo | Crítico | Alto | Bajo |
| **Gestión de Tareas / Hitos** | Bajo | Medio | Crítico | Bajo | Alto | Medio |
| **Inventario y Catálogo (SKU)** | Nulo | Bajo | Bajo | Medio | Alto | Crítico |
| **Liquidación de Comisiones** | Alto | Crítico | Medio | Alto | Medio | Alto |

**Cómo leerla:**

- **Finanzas** es crítica para todos: debe construirse primero y bien.
- **Agenda, Tareas e Inventario** tienen demanda muy dispareja: por eso son motores activables y no parte del núcleo.
- La **tarea simple** entre colaboradores (asignar, vencer, aprobar el cierre) es parte del **núcleo**. El motor de **Tareas e Hitos** agrega hitos, dependencias y cobro por avance, y sigue siendo propio del Clúster 3.
- El **Clúster 6** depende de un motor (Inventario) que el piloto no usa: "Nulo" en C1.
- El orden de construcción de motores debería seguir a los clientes reales, no a esta tabla.

## 10.4 Vacíos encontrados en el mapeo

| Vacío | Dónde se trata |
|-------|----------------|
| El negocio financiero del piloto no está en ningún clúster | ✅ Resuelto: módulo complementario ([NUC-Q-01](08-preguntas-abiertas.md#decisiones-tomadas)) |
| Restaurantes y comercio minorista no aparecen como vertical | ✅ Resuelto: vertical 6.3 ([NUC-Q-02](08-preguntas-abiertas.md#decisiones-tomadas)); hay que añadirla al documento de mapeo original |
| Comprobantes electrónicos no aparecen en ningún módulo | [NUC-Q-07](08-preguntas-abiertas.md) |
| "Punto de venta" se cita en 4.3 y 4.4, pero no figura como motor en la matriz | Tratar como motor cuando se aborde C4 o C6.3 |
| La "Contraparte con acceso propio" (reservas, consulta de estado, portal) aparece en C4 y C5 sin módulo asignado | Candidato a motor "Portal externo" |
