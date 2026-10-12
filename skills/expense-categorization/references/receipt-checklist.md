# Checklist de comprobante (borrador)

## Campos críticos (sin estos no hay borrador)

- total
- fecha
- nombre del proveedor o CUIT

## Campos esperados por tipo de comprobante

| Tipo | Campos esperados | IVA |
|---|---|---|
| Ticket / ticket-factura B o C | proveedor, CUIT, fecha, total | Incluido en el total, no se discrimina |
| Factura A | proveedor, CUIT, fecha, neto, IVA, total | Discriminado: registrar por separado |
| Comprobante sin CUIT (taxi, propina) | descripción, fecha, total | No aplica; confianza media como máximo |

## Umbrales de confianza

- **≥ 0,85** en total y fecha → se puede proponer borrador.
- **0,60 – 0,85** → proponer borrador y marcar los campos dudosos para el contador.
- **< 0,60** en total o fecha → `request_clarification`.

## Señales de duplicado

- mismo proveedor + mismo total + fecha ±3 días
- mismo número de comprobante
