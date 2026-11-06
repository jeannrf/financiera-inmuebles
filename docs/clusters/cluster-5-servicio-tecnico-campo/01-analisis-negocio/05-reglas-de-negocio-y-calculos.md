# 05. Reglas de negocio y cálculos

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

## Reglas

| ID | Regla | Vertical | Origen |
|----|-------|:--------:|--------|
| C5-RN-01 | No se ejecuta trabajo sin aprobación del cliente. Las excepciones se registran. | 5.1, 5.2 | [MAPEO] |
| C5-RN-02 | Todo trabajo nuevo requiere una aprobación adicional. | 5.1, 5.2 | [INFERIDO] |
| C5-RN-03 | El estado de ingreso del bien queda registrado y no se puede editar. | 5.1, 5.2 | Aplica NUC-RN-01 |
| C5-RN-04 | Mano de obra y repuestos siempre se separan en el ingreso y el margen. | Todas | [MAPEO] |
| C5-RN-05 | Un repuesto solo se consume desde una OT, y descuenta stock. | Todas | [INFERIDO] |
| C5-RN-06 | La tarifa de diagnóstico se descuenta si se aprueba la reparación. | 5.2 | [MAPEO] |
| C5-RN-07 | La garantía cubre el trabajo por el plazo configurado (por ejemplo, 90 días). | 5.2 | [MAPEO] |
| C5-RN-08 | La contraseña de un equipo se cifra, se audita su lectura y **se elimina al entregarlo**. | 5.2 | [INFERIDO] |
| C5-RN-09 | No se declara abandono sin avisos previos registrados. | 5.2 | [INFERIDO] |
| C5-RN-10 | Todo servicio de abono termina con certificado o constancia. | 5.3 | [MAPEO] |
| C5-RN-11 | La OT por siniestro separa lo que paga la aseguradora del deducible del cliente. | 5.1 | [INFERIDO] |

## Cálculos

```
Costo de OT           = Σ(horas × costo hora) + Σ(repuestos a costo) + servicios externos                 [MAPEO]
Margen de mano de obra = venta de mano de obra − costo de mano de obra
Margen de repuestos    = venta de repuestos − costo de repuestos
Rentabilidad de contrato = abono mensual − costo de cuadrilla asignada − insumos consumidos               [MAPEO]

Km por día            = (km actual − km visita anterior) / días entre visitas
Fecha próximo servicio = hoy + (km próximo servicio − km actual) / km por día
```

**Ejemplo: OT de taller**

| Concepto | Venta | Costo | Margen |
|----------|------:|------:|-------:|
| Mano de obra (3 h) | S/ 240 | S/ 90 | S/ 150 |
| Repuestos | S/ 400 | S/ 300 | S/ 100 |
| **Total** | **S/ 640** | **S/ 390** | **S/ 250 (39 %)** |

**Ejemplo: próximo cambio de aceite.** Con 2 400 km en 60 días (40 km/día), 12 000 km actuales y próximo cambio a los 15 000 km: faltan 3 000 km, es decir, unos **75 días**.
