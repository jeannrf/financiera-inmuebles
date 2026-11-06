# 02. Dominio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 2.1 Modelo común del clúster [INFERIDO]

```
Oportunidad (Expediente de venta)
├── Contacto y dueño comercial (vendedor)
├── Etapa del pipeline y probabilidad
├── Cotización (v1, v2, v3…) → Líneas de costo y precio
│     └── Versión aceptada ──► Contrato / Póliza / Pedido
│                               ├── Plan de pagos → Obligaciones → Pagos
│                               └── Costos reales → Margen del expediente
├── Tareas y trámites
└── Liquidación de comisiones (según reglas por rol)
```

| Concepto común | 2.1 Seguros | 2.2 Vehículos | 2.3 Instalaciones | 2.4 Viajes |
|----------------|-------------|---------------|-------------------|------------|
| **Lo que se cierra** | Póliza | Venta de vehículo | Proyecto | Expediente de viaje |
| **Cotización** | Comparativo por aseguradora | Precio + retoma + financiamiento | Equipos + materiales + mano de obra + viáticos | Vuelos + hoteles + traslados |
| **Cómo gana** | **Comisión de la aseguradora** | Margen de venta | Margen de proyecto | Margen sobre proveedores |
| **Cómo cobra** | La prima va a la aseguradora | Inicial + crédito | Hitos: 50 / 30 / 20 | Pagos parciales |
| **Recurrencia** | Renovación | Baja | Mantenimiento anual | Baja |
| **Terceros** | Aseguradora, perito | Banco, notaría, registros | Fabricante | Aerolínea, hotel, mayorista |

> **Diferencia de fondo:** en 2.1 y parcialmente en 2.4 el dinero del cliente **no es ingreso** del negocio. Si el P&L registra
> la prima como venta, queda falseado.

## 2.2 Especificación por vertical (del mapeo)

*Orientado a negocios con ciclos de venta consultivos, tickets medios/altos, manejo de cotizaciones complejas y esquemas de comisiones.*

### Arquitectura del clúster
* **Entidad Principal:** Oportunidad Comercial / Expediente de Venta.
* **Sub-entidades:** Cotizaciones/Propuestas versionadas, Pólizas/Contratos, Plan de pagos/Financiamiento, Liquidación de comisiones.
* **Conexión Financiera (P&L):** Proyección de ingresos según probabilidad de cierre (Forecast), cuentas por cobrar fraccionadas en cuotas y dispersión de comisiones a vendedores o brókers externos.

### Verticales

#### 2.1. Corredurías y Brókers de Seguros
* **Cobertura Operativa:**
  * Pipeline de emisión de nuevas pólizas y pipeline paralelo automático de renovaciones (alertas 60, 30 y 15 días antes del vencimiento).
  * Cartera de pólizas vigentes por ramo (Vida, Autos, Salud, Patrimoniales), aseguradora, bien asegurado y coberturas.
  * Módulo de seguimiento de siniestros (Recepción de reclamo → Peritaje → Liquidación de aseguradora).
* **Cobertura Financiera:** Conciliación de comisiones pagadas por las compañías aseguradoras vs. comisiones cedidas a sub-agentes comerciales, control de primas pendientes de pago.

#### 2.2. Concesionarias de Vehículos (Nuevos, Seminuevos y Consignación)
* **Cobertura Operativa:**
  * Inventario unitario de vehículos con trazabilidad de costos de alistamiento (chapa, pintura, trámites legales) previos a la venta.
  * Gestión de "Retoma" (Trade-in): Tasación del auto usado del cliente como parte de pago para la compra de otro vehículo.
  * Pipeline de venta e integración de trámites (crédito vehicular, seguro, transferencia notarial/registral, entrega de placas).
* **Cobertura Financiera:** Margen bruto real por vehículo (Precio Venta - Costo Adquisición - Gastos Alistamiento - Comisión Vendedor), control de vehículos en consignación (liquidación al dueño original).

#### 2.3. Empresas de Instalaciones Técnicas e Ingeniería Comercial (Solar, HVAC, Seguridad)
* **Cobertura Operativa:**
  * Flujo comercial-técnico: Captación de lead → Visita de levantamiento técnico → Dimensionamiento y Presupuesto → Aprobación → Ejecución de instalación.
  * Armado de presupuestos compuestos (Equipos + Materiales + Mano de obra + Viáticos) con cálculo de margen objetivo.
  * Activación de contrato de mantenimiento preventivo anual una vez finalizada la instalación.
* **Cobertura Financiera:** Cobro por hitos (ej. 50% anticipo, 30% contra entrega de equipos, 20% tras acta de conformidad), control de desviación entre el costo presupuestado y el costo real de instalación.

#### 2.4. Agencias de Viajes Corporativas y Operadores Turísticos (DMCs)
* **Cobertura Operativa:**
  * Constructor de itinerarios y cotizaciones a medida (Vuelos + Hoteles + Traslados + Experiencias) con gestión de pasajeros y documentación (pasaportes, visas).
  * Control de reservas y confirmaciones (Vouchers) con cada proveedor mayorista o local.
  * Calendario de salidas grupales con control de cupos bloqueados (Allotment).
* **Cobertura Financiera:** Manejo de multimoneda, control de pagos parciales de clientes vs. fechas límite de pago a proveedores (aerolíneas/hoteles) y cálculo de utilidad neta por expediente de viaje.
