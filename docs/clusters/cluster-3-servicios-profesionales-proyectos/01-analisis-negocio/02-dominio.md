# 02. Dominio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 2.1 Modelo común del clúster [INFERIDO]

```
Cuenta de cliente
├── Contrato de iguala → Obligación mensual + entregables comprometidos
└── Proyecto / Expediente / Obra / Búsqueda
     ├── Hitos y entregables → Obligaciones de cobro
     ├── Tareas ← Registro de horas (a costo hora de cada persona)
     ├── Gastos: propios o por cuenta del cliente
     ├── Subcontrataciones
     └── Centro de costo → Rentabilidad
```

| Concepto común | 3.1 Legal y contable | 3.2 Marketing y software | 3.3 Construcción | 3.4 RR. HH. |
|----------------|----------------------|--------------------------|------------------|-------------|
| **Proyecto** | Expediente, carpeta fiscal | Cuenta, sprint | Obra | Búsqueda de vacante |
| **Hito** | Actuación procesal, etapa | Fase, entregable | Certificación de avance | Terna, contratación |
| **Costo principal** | Horas de abogados | Horas, freelancers | Materiales, destajos | Horas de reclutador |
| **Dinero de terceros** | Tasas y timbres | Pauta publicitaria | Fondo de reparo retenido | No suele haber |
| **Cómo cobra** | Iguala, etapas, éxito | Fee mensual, fases | Certificaciones | Anticipo + cierre |
| **Plazo crítico** | Procesal o tributario | Entrega | Avance | Garantía del candidato |

> **Hallazgo:** "Gastos suplidos" (3.1) y "pauta publicitaria" (3.2) son el mismo mecanismo: **dinero del cliente que pasa por el negocio**.
> También coincide con la garantía de C1 y la prima de C2. Es candidato a una pieza del núcleo: *fondos de terceros*.

## 2.2 Especificación por vertical (del mapeo)

*Orientado a empresas que venden conocimiento, tiempo o entregables bajo esquemas de proyectos cerrados o igualas mensuales (retainers).*

### Arquitectura del clúster
* **Entidad Principal:** Proyecto / Expediente / Cuenta de Cliente.
* **Sub-entidades:** Hitos y Entregables, Tareas/Horas registradas, Contratos de Iguala (Retainers), Gastos reembolsables.
* **Conexión Financiera (P&L):** Rentabilidad por proyecto y por cliente (Ingresos Facturados - Costo Hora del Equipo - Subcontrataciones/Proveedores).

### Verticales

#### 3.1. Estudios Contables, Firmas Legales y Notarías
* **Cobertura Operativa:**
  * Gestión de expedientes judiciales/administrativos o carpetas fiscales por cliente, con línea de tiempo de actuaciones y vencimientos procesales/tributarios.
  * Separación clara entre clientes de "Iguala Mensual" (honorario fijo recurrente) y clientes por "Trámite/Caso" (cobro por etapas o éxito).
  * Repositorio documental estructurado para compartir entregables (balances, declaraciones, contratos) con el cliente.
* **Cobertura Financiera:** Registro de "Gastos Suplidos" o reembolsables (tasas judiciales, timbres, pagos notariales realizados a nombre del cliente) separados de los honorarios propios del estudio para no distorsionar el P&L.

#### 3.2. Agencias de Marketing, Publicidad y Desarrollo de Software
* **Cobertura Operativa:**
  * Gestión de servicios recurrentes (ej. manejo de redes, SEO, soporte técnico) con control de entregables mensuales comprometidos.
  * Gestión de proyectos puntuales (ej. desarrollo web, rebranding) divididos en sprints o fases con aprobación del cliente.
  * Asignación de especialistas o freelancers externos por tarea o proyecto.
* **Cobertura Financiera:** Separación del presupuesto de pauta publicitaria del cliente (Ad Spend en Meta/Google) respecto al Fee de agencia, control de pagos a freelancers y margen de contribución por cliente.

#### 3.3. Estudios de Arquitectura, Diseño de Interiores y Constructoras PyME
* **Cobertura Operativa:**
  * Presupuesto de obra estructurado por partidas y rubros (Preliminares, Estructura, Acabados, Instalaciones).
  * Control de avance físico de obra y emisión de Certificaciones de Avance para cobro al cliente.
  * Gestión de subcontratistas, órdenes de compra de materiales enviados a obra y control de adicionales no presupuestados (Change Orders).
* **Cobertura Financiera:** Flujo de caja por obra (Ingresos por certificaciones vs. Egresos por materiales y destajos), control de fondo de reparo/garantía retenido y comparativa de Presupuesto Original vs. Gasto Real Ejecutado.

#### 3.4. Consultoras de RRHH, Headhunting y Selección de Personal
* **Cobertura Operativa:**
  * Gestión de vacantes/búsquedas abiertas por empresa cliente con perfil del puesto y condiciones salariales.
  * Pipeline de candidatos por vacante (Filtro CV → Entrevista Consultora → Pruebas → Terna presentada al cliente → Contratado).
  * Seguimiento del período de garantía del candidato (ej. 3 meses tras la contratación).
* **Cobertura Financiera:** Facturación escalonada (Anticipo de inicio de búsqueda + Cierre a la firma de contrato del candidato) calculada como porcentaje del salario anual del puesto, más comisiones para los reclutadores.

## 2.3 Entidades adicionales de la vertical 3.3 (construcción)

Vienen del ejemplo de la fábrica en NUC-P-15:

- **Presupuesto de obra:** versión aprobada, nunca se sobrescribe.
- **Partida:** rubro (Preliminares, Estructura, Acabados, Instalaciones), unidad, metrado, precio unitario y costo por m².
- **Avance físico:** % ejecutado por partida y fecha.
- **Certificación:** cobro por lo avanzado.
- **Adicional (Change Order):** cambio aprobado por el cliente.
- **Orden de compra** y **subcontrato**, imputados a una partida.
- **Fondo de reparo:** % retenido hasta el fin de la garantía.
