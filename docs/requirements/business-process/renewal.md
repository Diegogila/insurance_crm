# Business Process — Renovacion

## Objetivo
Cada año las polizas son renovadas y entregadas a los clientes

## Actores involucrados
- Administrador
- Agente
- Asegurado o  Cliente
- Corporativo

## Disparador

Se acerca la fecha de vigencia de una poliza

## Precondiciones
- La poliza debe estar pagada
- Se renueva antes del fin de la vigencia de una poliza

## Flujo principal
1. Se acerca la fecha de fin de vigencia de una poliza
2. Corporativo envia a administrador propuestas de cotizacion de renovaciones.
3. Administrador acepta propuestas
4. Corporativo emite renovaciones
5. Corporativo entrega renovaciones a administracion
6. Administracion entrega renovaciones a agentes
7. Agentes reparten renovaciones a sus asegurados

## Flujos alternativos

### A1. Poliza de gastos medicos o daños casa
1. (1.1.1) Se acerca la fehca de fin de vigencia de una poliza
2. (1.1.2) Administracion solicita renovaciones
2. (1.1.3) Corporativo emite renovaciones

### A2. Vehiculo en status de salvamento
1. (2.1.1) Corporativo envia a administrador propuestas de cotizacion de renovaciones.
2. (2.1.2) Coorporativo solicita factura de vehiculo por status de salvamento para poder renovar
3. (2.1.3) Administracion solicita documentacion a agente o cliente
4. (2.1.4) Administracion entrega documentacion a corporativo
5. (2.1.5) Corporativo entrega renovacion a administracion

## Reglas relacionadas

## Resultado esperado
Las renovaciones del mes son emitidas correctamente

## Diagrama
```mermaid
flowchart TD
    A[Se acerca la fecha de fin de vigencia de una poliza]
    A1{¿Es GMM o Daños?}
    A2[Administrador solicita renovaciones a Corporativo]
    B[Corporativo envia a administrador propuestas de cotizacion de renovaciones]
    B1{¿Vehiculo con status salvamento?}
    B2[Corporativo pide doc adicional]
    B3[Administracion solicita doc a agente o cliente]
    B4[Administracion entrega doc a corporativo]
    C[Administrador acepta propuestas]
    D[Corporativo emite renovaciones]
    E[Corporativo entrega renovaciones a administracion]
    F[Administracion entrega renovaciones a agentes]
    G[Agentes reparten renovaciones a sus asegurados]

    A --> A1
    A1 -->|Si|A2
    A2 --> D
    A1 -->|No|B
    B --> B1
    B1 -->|Si|B2
    B1 -->|No|C
    C --> D
    B2 --> B3
    B3 --> B4
    B4 --> D
    D --> E
    E --> F
    F --> G