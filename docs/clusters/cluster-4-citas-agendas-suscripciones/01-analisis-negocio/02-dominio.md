# 02. Dominio

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## 2.1 Modelo común del clúster [INFERIDO]

```
Responsable de pago (Titular, Tutor, Propietario)
└── Persona atendida (Paciente, Alumno, Socio, Mascota)
     ├── Historial (Ficha clínica, asistencia, evolución)
     ├── Paquete / Membresía → Saldo de sesiones o vigencia
     └── Cita o Reserva ── Profesional + Recurso + Servicio + Horario
           └── Atendido → Consumo de saldo + Insumos + Comisión

Caja diaria ← Ventas y cobros por método de pago
```

| Concepto común | 4.1 Clínicas | 4.2 Academias | 4.3 Gimnasios | 4.4 Veterinarias |
|----------------|--------------|---------------|---------------|------------------|
| **Persona atendida** | Paciente | Alumno | Socio | Mascota |
| **Quien paga** | Paciente | Padre, madre o alumno | Socio | Propietario (1 a N mascotas) |
| **Recurso** | Consultorio, cabina | Aula | Sala, camas de Pilates | Consultorio, peluquería |
| **Reserva** | Cita individual | Matrícula en grupo | Lugar en una clase | Cita |
| **Venta típica** | Paquete de tratamiento | Matrícula + pensión | Membresía o pase | Consulta + producto |
| **Pago a profesional** | Comisión | Por hora dictada | Por clase | Comisión o sueldo |
| **Datos sensibles** | **Salud** | Menores de edad | Salud parcial | Datos del propietario |

## 2.2 Especificación por vertical (del mapeo)

*Orientado a negocios de atención al público que monetizan bloques de tiempo de profesionales, paquetes de sesiones o membresías periódicas.*

### Arquitectura del clúster
* **Entidad Principal:** Paciente / Alumno / Socio (Ficha de Historial) + Agenda/Turnero.
* **Sub-entidades:** Citas/Reservas, Paquetes de Sesiones / Membresías, Comisiones de Especialistas, Consumo de Insumos.
* **Conexión Financiera (P&L):** Caja diaria por método de pago (Efectivo, POS, Transferencia), control de ingresos diferidos (paquetes cobrados por adelantado) y liquidación de honorarios a profesionales.

### Verticales

#### 4.1. Clínicas Estéticas, Odontológicas, Fisioterapia y Centros de Salud
* **Cobertura Operativa:**
  * Agenda multi-profesional y multi-consultorio/cabina con estados de cita (Confirmada, En sala de espera, Atendido, No asistió).
  * Ficha e historial clínico evolutivo del paciente, odontograma/esquema corporal, consentimientos informados firmados y fotografías de antes/después.
  * Venta y control de "Bonos o Paquetes de Tratamiento" (ej. Paquete de 10 sesiones de láser: el sistema descuenta automáticamente 1 sesión cada vez que asiste).
* **Cobertura Financiera:** Liquidación automática de comisiones médicas (porcentaje o monto fijo por tratamiento realizado, descontando costos de laboratorio o insumos), control de presupuestos dentales/estéticos financiados en cuotas.

#### 4.2. Centros Educativos Privados, Academias (Idiomas, Música, Deportes)
* **Cobertura Operativa:**
  * Gestión de ciclos lectivos, cursos, niveles, horarios y asignación de aulas y profesores.
  * Proceso de matriculación de alumnos, control de cupos máximos por grupo y registro de asistencia e inasistencias.
  * Gestión de clases particulares (por bolsas de horas) vs. cursos grupales regulares.
* **Cobertura Financiera:** Emisión de cargos recurrentes por matrícula y pensiones/mensualidades, descuentos por hermanos o pronto pago, control estricto de alumnos morosos y liquidación de pagos a docentes por hora dictada.

#### 4.3. Gimnasios Boutique, Estudios de Yoga, Pilates y Crossfit
* **Cobertura Operativa:**
  * Calendario de clases grupales con cupo limitado (ej. 12 camas de Pilates Reformer por turno) y reserva de lugar por parte del socio.
  * Gestión de planes y membresías (Mensual, Trimestral, Anual, Pase de 8 o 12 clases al mes) con congelamiento de días por viaje o lesión.
  * Control de vencimientos y alertas de renovación automática.
* **Cobertura Financiera:** Métricas de retención y bajas (Churn Rate), ingresos recurrentes mensuales (MRR), venta rápida de productos de mostrador (agua, suplementos, indumentaria) integrada a la caja diaria.

#### 4.4. Clínicas Veterinarias y Pet Shops
* **Cobertura Operativa:**
  * Estructura de doble entidad: Propietario (Humano que paga) → Múltiples Mascotas (Pacientes con ficha de especie, raza, peso y edad).
  * Historial médico veterinario, internaciones y motor automático de recordatorios de medicina preventiva (Vacunas anuales, desparasitaciones, controles) vía WhatsApp/Email.
  * Agenda separada para Consultorio Médico y para Peluquería/Baño (Grooming).
* **Cobertura Financiera:** Punto de venta (POS) híbrido que unifica en un solo ticket el cobro de servicios clínicos + medicamentos utilizados + alimentos o accesorios del Pet Shop.
