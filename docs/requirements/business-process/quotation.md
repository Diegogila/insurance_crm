# Business Process — Cotizacion

## Objetivo
Tiene el propocito de informar a los clientes el precio de prima de la poliza en caso de solicitarla

## Actores involucrados
- Administrador
- Agente
- Asegurado o  Cliente
- Corporativo

## Disparador

Cliente se acerca a agente para solciitar una cotizacion.

## Precondiciones
- En caso de ser un vehiculo, el vehiculo debe existir
- En caso de vehiculo se debe contar con targeta de circulacion o factura del vehiculo

## Flujo principal
1. El cliente se acerca a agente
2. Agente solicita a administrador cotizacion con condiciones de cliente y entrega documentacion del vehiculo
3. Administrador cotiza vehiculo de aseguradora
4. Administrador entrega cotizacion a agente

## Flujos alternativos

### A1. Vehiculo con status especial
1. (3.1.1) El vehiculo no cuenta con codigo de referencia y no puede ser localizado
2. (3.1.2) Se solicita cotizacion de poliza directamente a corporativo, agregando documentacion de referencia del vehiculo
3. (3.1.3) Corporativo entrega cotizacion a administracion
4. (3.1.4) Administracion entrega cotizacion a agente

## Reglas relacionadas

## Resultado esperado
La cotizacion es generada correctamente

## Diagrama
```mermaid
flowchart TD
    A[Cliente solicita cotizacion a agente]
    B[Agente solicita cotizacion a administracion]
    B1{¿Es un vehiculo?}
    B2{¿Se localizo el tipo de vehiculo?}
    B3[Se solicita cotizacion a corporativo]
    B4[Corporativo genera cotizacion de aseguradora]
    B5[Corporativo entrega cotizacion a administracion]
    C[Administracion genera cotizacion de aseguradora]
    D[Administracion entrega cotizacion a agente]
    E[Agente entrega cotizacion a cliente]

    A --> B
    B --> B1
    B1 -->|Si|B2
    B2 -->|Si|C
    B2 -->|No|B3
    B3 --> B4
    B4 --> B5
    B5 --> D
    B1 -->|No| C
    C --> D
    D --> E