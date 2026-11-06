# 05. Reglas de negocio y cálculos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Reglas

| ID | Regla | Vertical | Origen |
|----|-------|:--------:|--------|
| C4-RN-01 | Un profesional o recurso no puede tener dos citas que se traslapen. | Todas | [INFERIDO] |
| C4-RN-02 | Una clase no admite reservas por encima de su cupo. | 4.2, 4.3 | [MAPEO] |
| C4-RN-03 | Una sesión se descuenta **solo al marcar Atendido**; una inasistencia, según la política. | Todas | [MAPEO] |
| C4-RN-04 | Un paquete cobrado por adelantado es **ingreso diferido**, no ingreso del mes. | Todas | [MAPEO] |
| C4-RN-05 | El saldo de un paquete nunca es negativo y se calcula por sus movimientos. | Todas | [INFERIDO] |
| C4-RN-06 | La caja cerrada no se edita; un ajuste va como movimiento autorizado. | Todas | Aplica NUC-RN-01 y 11 |
| C4-RN-07 | Las notas clínicas no se editan ni borran: se corrigen con una nota nueva. | 4.1, 4.4 | [INFERIDO] |
| C4-RN-08 | El congelamiento extiende la vigencia y tiene un máximo por período. | 4.3 | [MAPEO] |
| C4-RN-09 | Una mascota siempre tiene un propietario, y el propietario es quien paga. | 4.4 | [MAPEO] |
| C4-RN-10 | Los descuentos (hermanos, pronto pago) son parámetros del negocio. | 4.2 | [MAPEO] |
| C4-RN-11 | Los datos de menores requieren el consentimiento del responsable. | 4.2 | [INFERIDO] |

## Cálculos

```
Ingreso reconocido por sesión = precio del paquete / sesiones del paquete
Ingreso diferido              = Σ (sesiones restantes × ingreso por sesión)

Comisión médica (4.1)         = (precio del tratamiento − costos de laboratorio e insumos) × % del profesional, o monto fijo   [MAPEO]
Pago a docente (4.2)          = horas dictadas × tarifa por hora                                                               [MAPEO]

MRR (4.3)                     = Σ membresías activas normalizadas a un mes                                                     [MAPEO]
Churn mensual (4.3)           = bajas del mes / socios activos al inicio del mes × 100                                         [MAPEO]

Ocupación                     = horas o lugares reservados / horas o lugares disponibles × 100
Diferencia de caja            = efectivo contado − (apertura + cobros en efectivo − egresos en efectivo)
```

**Ejemplo: paquete de 10 sesiones de láser por S/ 1 000**

| Momento | Caja | Ingreso del mes | Ingreso diferido |
|---------|-----:|----------------:|-----------------:|
| Se vende el paquete | + S/ 1 000 | S/ 0 | S/ 1 000 |
| Asiste a 3 sesiones en el mes | | S/ 300 | S/ 700 |

**MRR:** un plan trimestral de S/ 300 aporta S/ 100 al mes; 30 planes mensuales de S/ 150 aportan S/ 4 500.
