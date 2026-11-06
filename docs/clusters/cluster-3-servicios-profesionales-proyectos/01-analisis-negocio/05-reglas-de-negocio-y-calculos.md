# 05. Reglas de negocio y cálculos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Reglas

| ID | Regla | Vertical | Origen |
|----|-------|:--------:|--------|
| C3-RN-01 | Todo gasto se clasifica como **propio** o **por cuenta del cliente**. Este último no entra al P&L. | 3.1, 3.2 | [MAPEO] |
| C3-RN-02 | La pauta publicitaria se registra aparte del fee de agencia. | 3.2 | [MAPEO] |
| C3-RN-03 | Una hora solo cuenta si se imputa a una tarea de un proyecto activo. | 3.1, 3.2, 3.4 | [INFERIDO] |
| C3-RN-04 | El costo hora tiene fecha de vigencia y no cambia el costo de horas pasadas. | Todas | Aplica NUC-RN-01 |
| C3-RN-05 | Un vencimiento legal o tributario siempre tiene un responsable y alerta de escalamiento. | 3.1 | [INFERIDO] |
| C3-RN-06 | Un adicional requiere la **aprobación del cliente** antes de ejecutarse. | 3.2, 3.3 | [INFERIDO] |
| C3-RN-07 | El presupuesto aprobado es **línea base inmutable**; los cambios van como adicionales. | 3.3 | Aplica NUC-RN-01 |
| C3-RN-08 | La certificación acumulada no puede superar el 100 % del presupuesto vigente. | 3.3 | [INFERIDO] |
| C3-RN-09 | El fondo de reparo es dinero retenido por el cliente: se registra como cuenta por cobrar y se libera al vencer la garantía. | 3.3 | [MAPEO] |
| C3-RN-10 | Si el candidato sale durante la garantía, se aplica la reposición o devolución pactada. | 3.4 | [INFERIDO] |

## Cálculos

```
Rentabilidad = ingresos facturados − Σ(horas × costo hora) − subcontrataciones/proveedores   [MAPEO]

Margen %     = rentabilidad / ingresos facturados × 100

Honorario de búsqueda = % pactado × salario anual del puesto                                  [MAPEO]

Avance % de la obra   = Σ(avance de partida × costo de partida) / Σ costo de partidas

Certificación del período = (presupuesto vigente × avance %) − Σ certificado anterior
Retención de fondo de reparo = certificación del período × % de reparo
Neto a cobrar         = certificación del período − retención − amortización de anticipo

Desviación de partida = gasto real − presupuesto de la partida                                [MAPEO]
```

**Ejemplo: iguala que parece buena y no lo es**

| Concepto | Valor |
|----------|------:|
| Iguala mensual | S/ 3 000 |
| Horas consumidas | 40 h |
| Costo hora | S/ 70 |
| Costo del equipo | S/ 2 800 |
| **Rentabilidad** | **S/ 200 (6.7 %)** |

**Ejemplo: certificación de obra**

| Concepto | Valor |
|----------|------:|
| Presupuesto vigente | S/ 500 000 |
| Avance acumulado | 40 % = S/ 200 000 |
| Certificado anterior | S/ 150 000 |
| Certificación del período | S/ 50 000 |
| Fondo de reparo (5 %) | − S/ 2 500 |
| **Neto a cobrar** | **S/ 47 500** |
