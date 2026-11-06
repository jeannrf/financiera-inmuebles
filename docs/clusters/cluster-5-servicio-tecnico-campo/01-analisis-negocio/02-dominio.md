# 02. Dominio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 2.1 Modelo común del clúster [INFERIDO]

```
Cliente
└── Bien (Vehículo, Equipo, Instalación)
     └── Orden de Trabajo (OT)
          ├── Ingreso: fotos, estado, motivo
          ├── Diagnóstico → Presupuesto → Aprobación del cliente
          ├── Asignación: técnico, bahía o cuadrilla
          ├── Mano de obra + Repuestos consumidos (descuentan stock)
          ├── Control de calidad → Conformidad o firma
          └── Cobro + Garantía

Contrato de abono → genera OT periódicas (5.3)
```

| Concepto común | 5.1 Talleres | 5.2 Electrónica y TI | 5.3 Mantenimiento en sitio |
|----------------|--------------|----------------------|----------------------------|
| **Bien** | Vehículo (por placa) | Equipo (IMEI o serie) | Local, edificio, jardín |
| **Lugar** | Taller, bahía | Mostrador o domicilio | Donde está el cliente |
| **Disparador** | Falla o mantenimiento | Falla | Calendario del contrato |
| **Evidencia** | Inventario, fotos, km | Estado estético, accesorios | Certificado firmado |
| **Quién paga** | Cliente o aseguradora | Cliente | Cliente corporativo |
| **Modelo de ingreso** | Por OT | Por OT + diagnóstico | Abono + extras |

## 2.2 Especificación por vertical (del mapeo)

*Orientado a negocios que reparan bienes de clientes o desplazan personal técnico para ejecutar mantenimientos e instalaciones.*

### Arquitectura del clúster
* **Entidad Principal:** Orden de Trabajo (OT) / Ticket de Servicio.
* **Sub-entidades:** Bien intervenido (Vehículo, Equipo, Instalación), Diagnóstico y Presupuesto, Repuestos consumidos, Conformidad del cliente.
* **Conexión Financiera (P&L):** Separación de ingresos y márgenes entre Mano de Obra (Servicio) y Venta de Repuestos/Materiales.

### Verticales

#### 5.1. Talleres Mecánicos, Lubricentros y Chapa/Pintura
* **Cobertura Operativa:**
  * Recepción del vehículo por placa/patente con inventario de ingreso, fotos, kilometraje y motivo de ingreso reportado por el cliente.
  * Flujo de taller: Diagnóstico mecánico → Armado de presupuesto (Mano de obra + Repuestos) → Aprobación del cliente → Asignación de bahía/mecánico → Control de calidad → Entrega.
  * Historial completo de servicios por vehículo y alertas de próximo cambio de aceite o mantenimiento por kilometraje estimado.
* **Cobertura Financiera:** Costeo exacto de cada Orden de Trabajo (compras de repuestos específicos para ese auto + horas de mecánico), manejo de cobros a compañías de seguros (siniestros) vs. clientes particulares.

#### 5.2. Servicio Técnico de Electrónica, Línea Blanca, Maquinaria y Soporte TI
* **Cobertura Operativa:**
  * Emisión de orden de ingreso en mostrador o a domicilio con número de serie (IMEI/SN), estado estético, accesorios dejados y contraseña de desbloqueo si aplica.
  * Consulta de estado en línea para el cliente ("En revisión", "Esperando repuesto", "Presupuesto pendiente de aprobación", "Listo para retirar").
  * Gestión de garantías de reparación (ej. 90 días sobre el trabajo realizado) y control de inventario de piezas de recambio.
* **Cobertura Financiera:** Cobro de tarifa de diagnóstico/revisión anticipada (descontable si aprueba la reparación), control de equipos abandonados y margen neto por técnico reparador.

#### 5.3. Empresas de Mantenimiento Edilicio, Limpieza, Fumigación y Jardinería
* **Cobertura Operativa:**
  * Gestión de contratos de abono periódico con clientes corporativos o consorcios (ej. fumigación mensual o limpieza diaria).
  * Planificador de rutas y cuadrillas de trabajo con generación de certificados de servicio realizado (ej. Certificado de Desinfección con firma digital del cliente en el lugar).
  * Control de entrega de insumos, químicos, herramientas y uniformes al personal operativo.
* **Cobertura Financiera:** Rentabilidad por contrato recurrente (Abono Mensual - Costo de Cuadrilla Asignada - Insumos Consumidos), facturación masiva mensual de abonos más servicios extraordinarios.
