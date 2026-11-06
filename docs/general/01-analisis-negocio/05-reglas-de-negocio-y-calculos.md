# 05. Reglas de negocio y cálculos del núcleo

## 5.1 Reglas universales

Los números de las reglas originales se conservan para mantener la trazabilidad.

| ID | Regla | Origen |
|----|-------|--------|
| NUC-RN-01 | **Nada se borra:** montos y pagos históricos no se eliminan ni se sobrescriben. Un cambio crea un **registro nuevo con fecha de vigencia**. | [CONFIRMADO] "No es editar, sino colocarlo nuevo" |
| NUC-RN-02 | Una obligación toma el **valor vigente** en su período (el último con `fecha_vigencia ≤ inicio del período`). | [INFERIDO de NUC-RN-01] |
| NUC-RN-04 | El sistema **no decide solo** si un comprobante es válido; lo confirma una persona. La IA o el OCR solo sugieren. | [CONFIRMADO] |
| NUC-RN-11 | Un período **cerrado** no admite cambios. Solo se cierra si cumple las condiciones de cada paquete. | [CONFIRMADO] |
| NUC-RN-12 | La visibilidad de datos sensibles depende del rol. Por defecto, el operador **no ve** ganancias, rendimientos, valorizaciones ni totales. | [CONFIRMADO] |
| NUC-RN-13 | Los usuarios operativos pueden ser N, y el cargo determina los privilegios. | [CONFIRMADO] |
| NUC-RN-15 | Los gastos registrados por un operador pueden requerir **aprobación del dueño**. | [CONFIRMADO] |
| NUC-RN-18 | Una organización puede tener **N negocios**, cada uno con su objetivo mensual. | [CONFIRMADO] |
| NUC-RN-20 | **Aislamiento:** ningún dato cruza entre organizaciones, ni siquiera para consultas de historial. | [EQUIPO] |
| NUC-RN-21 | Las búsquedas de personas por documento se limitan a la **organización**. No se comparte morosidad entre clientes. | [INFERIDO → NUC-Q-06] |
| NUC-RN-22 | Toda excepción al flujo normal y todo acceso de soporte queda en auditoría. | [INFERIDO] |
| NUC-RN-23 | La IA **no publica** configuraciones ni ejecuta acciones sobre datos reales sin confirmación humana. | [EQUIPO] |
| NUC-RN-24 | Las reglas de un rubro van en su paquete o plantilla, **nunca** en el núcleo. | [EQUIPO] |
| NUC-RN-25 | Los importes, impuestos, umbrales y pesos son **parámetros**, no valores fijos en el código. | [CONFIRMADO, ver NUC-RNF-12] |
| NUC-RN-27 | El dinero de terceros (garantías, primas, gastos suplidos, pauta) **no es ingreso** y no entra al P&L. | [INFERIDO de C1, C2 y C3] |
| NUC-RN-26 | Los cálculos tributarios **calculan y reportan**; no presentan declaraciones ante SUNAT. | [CONFIRMADO en fases] |

## 5.2 Cómo cambia cada regla según el clúster

Varias reglas nacieron pensando en alquileres, donde hay pocos pagos al mes. No se aplican igual en todos los rubros. [INFERIDO]

| Regla | C1 Activos | C2 Comercial | C3 Proyectos | C4 Citas | C5 Técnico | C6 Comercio |
|-------|------------|--------------|--------------|----------|------------|-------------|
| **Verificación del comprobante** | Pago por pago | Pago por pago | Pago por pago | Por **cierre de caja** diario | Por OT o caja | Por **cierre de turno** y conciliación |
| **Unidad de centro de costo** | Unidad o activo | Expediente | Proyecto o cliente | Sede o profesional | OT o contrato | Línea, tienda o pedido |
| **Condición de cierre** | Cuotas y prorrateos conciliados | Comisiones liquidadas | Horas y gastos cargados | Cajas cerradas | OT facturadas | Cajas y Kardex conciliados |
| **Indicador del tablero** | Alquiler cobrado | Margen cerrado o forecast | Facturado o margen | Caja o MRR | Facturado | Ventas o margen bruto |

> Con muchas ventas al día no es posible que una persona verifique cada pago. **La política de verificación debe
> ser configurable por paquete**, sin perder el principio de NUC-RN-04: siempre responde una persona.

## 5.3 Tablero: estado del negocio frente al objetivo


```
avance % = monto real del mes / objetivo del mes × 100
Verde si avance ≥ 100 % (o ≥ lo esperado a la fecha)   ·   Rojo si está por debajo
```
Ejemplo del cliente: objetivo 120 al mes de octubre; real 116 → rojo; real 160 → verde.
Rojo también significa que "alguien no ha pagado" → al hacer clic se ven las cuentas pendientes.
[PREGUNTA NUC-Q-26: ¿qué representa exactamente el "monto" de la tarjeta: ingresos del mes, acumulado del año o patrimonio?]
