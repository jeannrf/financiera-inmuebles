# 02-srs (general)

Especificación de Requerimientos de Software v1.0 de la plataforma transversal, correspondiente a **Capa 1 (Núcleo)** y **Capa 2 (Motores)**.

## Documentos publicados

| Documento | Alcance | Cobertura normativa | Estado |
|-----------|---------|---------------------|:------:|
| [01. SRS del Núcleo SaaS Transversal (`NUC`)](01-srs-nucleo-saas.md) | **Capa 1:** Contextos `K1`–`K9`, contratos de extensión (`E1`–`E7`, `D1`–`D4`, `NUC-EV-01`–`15`), despliegue y atributos de datos | `NUC-RF-01`–`24`, `30`–`45`, `80`–`82` (`85` absorbido); `NUC-RNF-01`–`23`; `NUC-CU-01`–`24`; `NUC-I-01`–`14`; cierre de los 13 puntos de §15 | ✅ v1.0 (`FIN-04`) |
| [02. Especificación del Motor de Cobro Recurrente (`MCR`)](02-especificacion-motor-cobro-recurrente.md) | **Capa 2:** Contratos periódicos, participantes, `TarifaVigencia` histórica inmutable (`NUC-RN-01`/`02`), regla de mes corto e idempotencia `E1` | `MCR-RF-01`–`10`; `MCR-RN-01`–`08`; `MCR-I-01`–`06`; trazabilidad hacia `C1`, `C3`, `C4` y `C5` | ✅ v1.0 (`FIN-04`) |

> **Regla contra la duplicación:** los SRS de cada clúster (`docs/clusters/cluster-N/.../02-srs/`, p. ej. `FIN-05`) y del módulo complementario (`docs/modulos/.../02-srs/`, p. ej. `FIN-06`) referencian directamente estos dos documentos y especifican **únicamente** las entidades, reglas y cálculos particulares de su vertical.
