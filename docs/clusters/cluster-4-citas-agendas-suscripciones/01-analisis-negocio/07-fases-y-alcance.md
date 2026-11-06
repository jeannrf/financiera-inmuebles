# 07. Fases y alcance

> **Hipótesis sin validar:** aún no hay cliente real en este clúster. `[MAPEO]` viene del documento de mapeo de verticales; `[INFERIDO]` es deducción del equipo. Validar con el primer cliente antes del SRS.

**Dependencias:** núcleo, motor de cobro recurrente y un nuevo motor de **Agenda**. También servicios de caja diaria y, más adelante, punto de venta y portal externo.

**Vertical de entrada sugerida: 4.3 Gimnasios y estudios** [INFERIDO]: no tiene datos clínicos y su complejidad legal es menor. **4.1 Clínicas** tiene mayor riesgo regulatorio y conviene dejarla para después, salvo que el primer cliente sea de ese rubro.

| Fase | Contenido |
|------|-----------|
| **MVP del clúster** | Agenda, reservas, paquetes, membresías, caja y recordatorios |
| **Vertical de entrada** | Clases con cupo, planes, congelamiento y MRR |
| **Ampliación** | Liquidación de honorarios, ingresos diferidos, portal de reservas |
| **Otras verticales** | 4.2 (matrículas) · 4.4 (mascotas, ticket híbrido) · 4.1 (historia clínica) |

**Fuera de alcance inicial:**

- Telemedicina, recetas electrónicas o conexión con laboratorios.
- Conexión con aseguradoras de salud.
- Control físico de acceso (torniquetes).
- Aula virtual o contenidos educativos.
