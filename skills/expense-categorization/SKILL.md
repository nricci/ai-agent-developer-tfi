---
name: expense-categorization
description: Convierte la imagen de un recibo o comprobante de gasto en un borrador contable trazable para QuickBooks. Identifica proveedor, cuenta contable, impuestos y posibles duplicados, y pide aclaración cuando faltan datos. Usar para recibos, tickets, facturas de gasto o rendiciones.
metadata:
  course-version: "0.1.0"
  course-activation: "recibo|ticket|comprobante|factura|gasto|rendición|rendicion"
  course-negative-signals: "factura de venta|cobranza|sueldo|liquidación"
  course-tool-hints: "extract_receipt_data|search_vendors|recall_vendor_categorization|list_expense_accounts|find_duplicate_expenses|propose_expense_draft|request_clarification"
  course-resources: "references/categorization-rules.md|references/receipt-checklist.md"
  course-tags: "accounting|expenses|receipts|quickbooks"
---

# Expense Categorization

## Workflow

1. Extraé los datos del recibo antes de cualquier otra acción.
2. Verificá los campos críticos con `references/receipt-checklist.md`. Si falta el total o la fecha, o su confianza es baja, pedí aclaración: no adivines.
3. Identificá el proveedor: primero por CUIT, después por nombre aproximado. Si hay más de un candidato, elegí el más probable y marcá el match como ambiguo.
4. Consultá el historial del contador para ese proveedor. Si existe, tiene prioridad sobre las reglas genéricas.
5. Si no hay historial, elegí la cuenta con `references/categorization-rules.md` y bajá la confianza.
6. Buscá duplicados (mismo proveedor, mismo total, fecha ±3 días) antes de proponer.
7. Proponé el borrador con una justificación breve de cada decisión.

## Reglas

- Un borrador es una propuesta: nunca equivale a registrar el gasto.
- No inventes montos, fechas, CUIT ni proveedores.
- Si el comprobante es Factura A, registrá el IVA discriminado por separado.
- Registrá siempre la moneda original del comprobante.
- Si el proveedor no existe, proponé su alta dentro del borrador; no lo crees vos.

## Ejemplo

Ticket de YPF por ARS 45.000 con CUIT coincidente y dos imputaciones previas
a "Combustibles y movilidad": match exacto, cuenta tomada del historial,
confianza alta, sin duplicados → `propose_expense_draft`.

Ticket borroso donde no se lee el total → `request_clarification` con la
pregunta "¿Cuál es el total del ticket de la estación de servicio del 10/10?".
