# Business Process — Cotizacion

## Objetivo
El proceso tiene el objetivo de dar de baja la poliza de seguro

## Actores involucrados
- Administrador
- Agente
- Asegurado o  Cliente
- Corporativo

## Disparador

Cliente solicita cancelacion de su poliza de seguro.

## Precondiciones
- Polia debe estar activa

## Flujo principal
1. El cliente solicita la cancelacion de su poliza
2. Administrador revisa status de poliza
3. El cliente escribe y firma solicitud de cancelacion de su poliza
4. Administrador recibe carta solicitud firmada con identificacion
5. Administrador cancela poliza
6. Administrador notifica a cliente o agente

## Flujos alternativos

### A1. Poliza de gastos medicos mayores
1. (3.1.1) El cliente escribe y firma solicitud de cancelacion de su poliza
2. (3.1.2) Administrador entrega a agente formatos de cancelacion para que cliente llene
3. (3.1.3) Cliente llena y firma formatos
4. (3.1.4) Administrador recibe documentacion
5. (3.1.5) Administrador solicita cancelacion a corporativo y entrega documentacion
6. (3.1.6) Corporativo cancela poliza
7. (3.1.7) Administrador notifica a cliente o agente

### A2. Poliza pagada
1. (2.1.1) Administrador revisa status de poliza
2. (2.1.1) El cliente escribe y firma solicitud de cancelacion de su poliza
3. (2.1.2) Cliente llena y firma solciitud de devolucion de primas no devengadas
4. (2.1.3) Administrador recibe cartas solicitud firmada con identificacion y estado de cuenta
5. (2.1.4) Administrador solicita cancelacion a corporativo y entrega documentacion
6. (2.1.5) Corporativo cancela poliza
7. (2.1.6) Administrador notifica a cliente o agente

### A3. Poliza descontada por nomina
1. (2.2.1)Administrador revisa status de poliza
2. (2.2.2) El cliente escribe y firma solicitud de cancelacion de su poliza
5. (2.2.3)Administrador cancela poliza
4. (2.2.4)Administrador emite cartas de cambio de descuento en su nomina
5. (2.2.5)Cliente firma cartas y envia junto con identifiacion y talon de nomina
6. (2.2.6)Administrador entrega cartas a cliente o agente
7. (2.2.7)Administrador recibe documentacion firmada
8. (2.2.8)Administrador envia cartas firmadas a institucion financiera para baja de descuento
9. (2.2.9)Administrador notifica a cliente o agente

## Reglas relacionadas

## Resultado esperado
La poliza quedara cancelada sin futuros cobros

## Diagrama
```mermaid
flowchart TD
    A[Cliente solicita la cancelación de su póliza] --> B[Administrador revisa status de la póliza]

    B --> C{¿Qué tipo de cancelación aplica?}

    C -->|Cancelación estándar| D[Cliente escribe y firma solicitud de cancelación]
    D --> E[Administrador recibe solicitud firmada con identificación]
    E --> F[Administrador cancela póliza]
    F --> G[Administrador notifica a cliente o agente]

    C -->|Póliza de gastos médicos mayores| H[Cliente escribe y firma solicitud de cancelación]
    H --> I[Administrador entrega al agente formatos de cancelación]
    I --> J[Cliente llena y firma formatos]
    J --> K[Administrador recibe documentación]
    K --> L[Administrador solicita cancelación a corporativo y entrega documentación]
    L --> M[Corporativo cancela póliza]
    M --> N[Administrador notifica a cliente o agente]

    C -->|Póliza pagada| O[Cliente escribe y firma solicitud de cancelación]
    O --> P[Cliente llena y firma solicitud de devolución de primas no devengadas]
    P --> Q[Administrador recibe solicitud firmada, identificación y estado de cuenta]
    Q --> R[Administrador solicita cancelación a corporativo y entrega documentación]
    R --> S[Corporativo cancela póliza]
    S --> T[Administrador notifica a cliente o agente]

    C -->|Póliza descontada por nómina| U[Cliente escribe y firma solicitud de cancelación]
    U --> V[Administrador cancela póliza]
    V --> W[Administrador emite cartas de cambio de descuento en nómina]
    W --> X[Cliente firma cartas y las envía junto con identificación y talón de nómina]
    X --> Y[Administrador entrega cartas a cliente o agente]
    Y --> Z[Administrador recibe documentación firmada]
    Z --> AA[Administrador envía cartas firmadas a institución financiera para baja de descuento]
    AA --> AB[Administrador notifica a cliente o agente]