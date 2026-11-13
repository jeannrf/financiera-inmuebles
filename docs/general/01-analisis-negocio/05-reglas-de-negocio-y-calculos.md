# 05. Reglas de negocio y cálculos del núcleo

## 5.1 Reglas universales

Los números de las reglas originales se conservan para mantener la trazabilidad.

| ID | Regla | Origen |
|----|-------|--------|
| NUC-RN-01 | **Nada se borra:** montos y pagos históricos no se eliminan ni se sobrescriben. Un cambio crea un **registro nuevo con fecha de vigencia**. | [CONFIRMADO] "No es editar, sino colocarlo nuevo" |
| NUC-RN-02 | Una obligación toma el **valor vigente** en su período (el último con `fecha_vigencia ≤ inicio del período`). | [INFERIDO de NUC-RN-01] |
| NUC-RN-04 | El sistema **no decide solo** si un comprobante es válido; lo confirma una persona. La IA o el OCR solo sugieren. | [CONFIRMADO] |
| NUC-RN-11 | Un período **cerrado** no admite cambios. Solo se cierra si cumple las condiciones de cada paquete. | [CONFIRMADO] |
| NUC-RN-12 | La visibilidad de datos sensibles depende del rol. Por defecto, el operador **no ve** ganancias, rendimientos, valorizaciones ni totales. Sí ve los **montos individuales** que necesita para operar (por ejemplo, la cuota de un cliente y su comprobante). | [CONFIRMADO; reconfirmado en el cuestionario del 10/Nov/2026] |
| NUC-RN-30 | **Sin agregados para el operador:** ninguna pantalla, lista, exportación o reporte que vea un operador muestra **sumas, subtotales ni conteos de dinero** (recaudación del día, de la semana o del mes). Motivo del cliente: con los totales, el operador puede deducir las ganancias del negocio y usarlas para negociar su sueldo. | [CONFIRMADO — cuestionario P9] |
| NUC-RN-13 | Los usuarios operativos pueden ser N, y el cargo determina los privilegios. | [CONFIRMADO] |
| NUC-RN-15 | Los gastos registrados por un operador pueden requerir **aprobación del dueño**. | [CONFIRMADO] |
| NUC-RN-18 | Una organización puede tener **N negocios**, cada uno con su objetivo mensual. | [CONFIRMADO] |
| NUC-RN-20 | **Aislamiento:** ningún dato cruza entre organizaciones, ni siquiera para consultas de historial. | [EQUIPO] |
| NUC-RN-21 | Las búsquedas de personas por documento se limitan a la **organización**. No se comparte morosidad entre clientes. | [CONFIRMADO — cliente piloto, 13/Nov/2026; cierra NUC-Q-06] |
| NUC-RN-22 | Toda excepción al flujo normal y todo acceso de soporte queda en auditoría. | [INFERIDO] |
| NUC-RN-23 | La IA **no publica** configuraciones ni ejecuta acciones sobre datos reales sin confirmación humana. | [EQUIPO] |
| NUC-RN-24 | Las reglas de un rubro van en su paquete o plantilla, **nunca** en el núcleo. | [EQUIPO] |
| NUC-RN-25 | Los importes, impuestos, umbrales y pesos son **parámetros**, no valores fijos en el código. | [CONFIRMADO, ver NUC-RNF-12] |
| NUC-RN-27 | El dinero de terceros (garantías, primas, gastos suplidos, pauta) **no es ingreso** y no entra al P&L. | [INFERIDO de C1, C2 y C3] |
| NUC-RN-28 | Una tarea solo pasa a **Cerrada** cuando la aprueba quien la asignó o el dueño. El responsable no puede cerrarla solo. | [CONFIRMADO — PPT cliente] |
| NUC-RN-29 | Los datos con valor tributario se conservan **10 años** desde el cierre del ejercicio; antes de ese plazo solo se pueden archivar, no borrar. | [CONFIRMADO — PPT cliente] |
| NUC-RN-26 | Los cálculos tributarios **calculan y reportan**; no presentan declaraciones ante SUNAT. | [CONFIRMADO en fases] |

## 5.2 Cómo cambia cada regla según el clúster

Varias reglas nacieron pensando en alquileres, donde hay pocos pagos al mes. No se aplican igual en todos los rubros. [INFERIDO]

| Regla | C1 Activos | C2 Comercial | C3 Proyectos | C4 Citas | C5 Técnico | C6 Comercio |
|-------|------------|--------------|--------------|----------|------------|-------------|
| **Verificación del comprobante** | Pago por pago | Pago por pago | Pago por pago | Por **cierre de caja** diario | Por OT o caja | Por **cierre de turno** y conciliación |
| **Unidad de centro de costo** | Unidad o activo | Expediente | Proyecto o cliente | Sede o profesional | OT o contrato | Línea, tienda o pedido |
| **Condición de cierre** | Cuotas y prorrateos conciliados | Comisiones liquidadas | Horas y gastos cargados | Cajas cerradas | OT facturadas | Cajas y Kardex conciliados |
| **Indicador del tablero** | Alquiler **cobrado** [CONFIRMADO] | Margen cerrado o forecast | Facturado o margen | Caja o MRR | Facturado | Ventas o margen bruto |
| **Meta del negocio** | **Ocupación total** (ninguna unidad libre) [CONFIRMADO] | Crecimiento de clientes [CONFIRMADO, genérico] | Crecimiento de clientes | Crecimiento de clientes o socios | Crecimiento de clientes | Crecimiento de clientes |

> Con muchas ventas al día no es posible que una persona verifique cada pago. **La política de verificación debe
> ser configurable por paquete**, sin perder el principio de NUC-RN-04: siempre responde una persona.

## 5.3 Tablero: estado del negocio frente al objetivo


```
avance % = monto real del mes / objetivo del mes × 100
Verde si avance ≥ 100 % (o ≥ lo esperado a la fecha)   ·   Rojo si está por debajo
```
Ejemplo del cliente: objetivo 120 al mes de octubre; real 116 → rojo; real 160 → verde.
Rojo también significa que "alguien no ha pagado" → al hacer clic se ven las cuentas pendientes.

**Respuesta a NUC-Q-26 (cliente piloto, 10/Nov/2026)** [CONFIRMADO]:

- El **monto real** de la tarjeta son los **ingresos efectivamente cobrados** en el mes (caja), no lo facturado.
- La **meta** depende del tipo de negocio, y por eso la define cada paquete (NUC-RN-24):
  - en un negocio de **alquiler** (C1), la meta es que **todas las unidades estén alquiladas** y ninguna quede libre;
  - en los **demás negocios**, la meta es que **crezcan los clientes**.
- Por eso la tarjeta tiene **dos datos**: el **monto cobrado frente al objetivo** (común a todos) y un **indicador de meta**
  propio del paquete (ocupación en C1, número de clientes activos frente al mes anterior en los demás). [PROPUESTO]

```
Indicador de meta (C1)       = unidades ocupadas / unidades alquilables × 100      → verde solo si es 100 %
Indicador de meta (genérico) = clientes activos del mes − clientes activos del mes anterior   → verde si es > 0
```

El detalle de C1 está en [C1, B8](../../clusters/cluster-1-activos-alquileres-espacios/01-analisis-negocio/05-reglas-de-negocio-y-calculos.md#b8-indicadores-del-tablero-cobranza-y-ocupación).
