# ReceiptFlow

Agente que convierte fotos de recibos en borradores de gasto para QuickBooks Online y los registra solo después de la aprobación del contador.

> **Estado:** Parcial 1 — idea, caso de uso, alcance y arquitectura preliminar.
> El detalle de esta entrega está en [`docs/parcial-1.md`](docs/parcial-1.md).

## 1. Nombre del proyecto

ReceiptFlow — agente de carga de gastos desde recibos.

## 2. Integrantes

- Nicolás Ricci

## 3. Problema

Cargar gastos a partir de recibos es manual, repetitivo y propenso a errores (montos mal tipeados, cuentas mal elegidas, duplicados, proveedores repetidos), pero no se puede automatizar a ciegas porque un asiento mal registrado tiene impacto contable. Ver [Parcial 1 §1](docs/parcial-1.md#1-problema).

## 4. Usuario / destinatario

- **Empleado:** sube la foto del recibo.
- **Contador:** revisa, corrige, aprueba o rechaza los borradores antes de que se registren.

## 5. Descripción

Empleado sube recibo → el agente extrae datos, identifica proveedor, sugiere cuenta, chequea duplicados → propone un borrador (o pide aclaración) → el contador aprueba, modifica o rechaza → lo aprobado se registra en QuickBooks. Ver [Parcial 1 §3](docs/parcial-1.md#3-caso-de-uso).

## 6. Arquitectura

Agente único con tools de lectura, una skill de imputación contable, memoria de correcciones en SQLite y HITL antes de toda escritura externa. Diagrama en [Parcial 1 §6](docs/parcial-1.md#6-arquitectura-preliminar).

## 7. Decisiones técnicas

_Preliminares en [Parcial 1 §6](docs/parcial-1.md#6-arquitectura-preliminar). Se completan en el Parcial 2._

## 8. Instalación

_Pendiente._

## 9. Configuración

_Pendiente. Variables previstas en [`.env.example`](.env.example)._

## 10. Ejecución

_Pendiente._

## 11. Uso

_Pendiente._

## 12. Evaluación

_Pendiente. Plan en [Parcial 1 §9](docs/parcial-1.md#9-plan-de-evaluación-preliminar)._

## 13. Limitaciones

Ver alcance en [Parcial 1 §4](docs/parcial-1.md#4-alcance).
