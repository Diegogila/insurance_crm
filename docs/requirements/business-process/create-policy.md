# Business Process — Emision de poliza

## Objetivo
Es la base principal del negocio el general nuevas polizas para posteriormente cobrar las comisiones procedentes

## Actores involucrados
- Administrador
- Agente
- Asegurado o  Cliente
- Aseguradora
- Corporativo

## Disparador

Cliente acepta cotizacion proporcionada y solicita la emision con el agente.

## Precondiciones
- En caso de ser un vehiculo, el vehiculo debe existir
- Que el cliente no cuente con una poliza activa con la misma compañia
- El cliente debe contar con toda la documentacion para poder emitir

## Flujo principal
1. El cliente acepta cotizacion proporcionada por el agente
2. El agente solicita la emision a administracion
3. Administrador recibe documentacion
4. Administrador emite la poliza
5. La aseguradora entrega la poliza
6. Se registra la poliza en base de datos
7. Administrador entrega poliza y recibo o formato de financiamiento a agente
8. Agente entrega poliza a cliente

## Flujos alternativos

### A1. Vehiculo con status especial
1. (4.1.1) Al intentar emitir la poliza el sistema interno de la aseguradora rechaza la emision directa por identificar que el vehiculo tiene un status especial
2. (4.1.2) Se solicita emision de poliza directamente a corporativo, agregando documentacion adicional en caso de necesitarse
3. (4.1.3) Aseguradora entrega poliza a corporativo
4. (4.1.4) Corporativo entrega poliza a administracion

### A2. Mas de dos polizas anteriores canceladas por pago
1. (4.2.1) Al intentar emitir la poliza el sistema interno de la aseguradora rechaza la emision directa por tener mas de dos polizas anteriores canceladas por pago
2. (4.2.2) Administrador solicita pago anticipado antes de emitir
3. (4.2.3) Cliente paga poliza y entrega comprobante
4. (4.2.4) Se solicita emision de poliza directamente a corporativo, agregando el comprobante a la solicitud
5. (4.2.5) Aseguradora entrega poliza a corporativo
6. (4.2.6) Corporativo entrega poliza a administracion


### A3. Poliza de gastos medicos mayores
1. (3.1.1) El administrador recibe documentacion
2. (3.1.2) Administrador manda documentacion a coorporativo para emision
3. (3.1.3) Aseguradora entrega poliza a corporativo
4. (3.1.4) Corporativo entraga poliza a administrador

## Reglas relacionadas

## Resultado esperado
La poliza es generada y registrada correctamente

## Diagrama
```mermaid
flowchart TD
    A[Poliza solicitada]
    B[Se recibe documentacion]
    C{¿Es GMM?}
    D[Se envia documentos a corporativo para emision]
    E{¿Status especial?}
    F[Administracion emite poliza]
    G[Corporativo entrega poliza a Admin]
    H[Administracion entrega poliza a agente]
    I[Agente entrega poliza a cliente]
    


    A --> B
    B --> C
    C -->|Si| D
    C -->|No| E
    E -->|Si| D
    E -->|Si| F
    D --> G
    G --> H
    F --> H
    H --> I