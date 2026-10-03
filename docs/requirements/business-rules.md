# Business Rules

## Convención de identificadores

Las reglas utilizan el siguiente formato:

```text
BR-XXX
```

Ejemplo:

```text
BR-001
BR-002
BR-003
```

---

## Póliza

### BR-001 — Una póliza cancelada no puede considerarse activa

**Descripción:**  
Una póliza cuyo estado sea cancelado no puede mantener simultáneamente un estado activo.

**Aplica a:**

- Póliza

**Condición:**

```text
estado_póliza = CANCELADA
```

**Resultado esperado:**

La póliza debe considerarse no activa.

**Excepciones:**

Ninguna identificada.

---

### BR-002 — La prima de una póliza no puede ser negativa

**Descripción:**  
La prima total y la prima neta de una póliza deben tener valores iguales o mayores a cero.

**Aplica a:**

- Póliza
- Prima

**Condición:**

```text
prima_total >= 0
prima_neta >= 0
```

**Resultado esperado:**

El sistema no debe aceptar una póliza con prima total o prima neta negativa.

**Excepciones:**

Ninguna identificada.

---

### BR-003 — El número de recibos depende de la forma de pago

**Descripción:**  
La cantidad de recibos asociados a una póliza debe corresponder con la forma de pago seleccionada.

**Aplica a:**

- Póliza
- Recibo
- Forma de pago

**Resultado esperado:**

La póliza debe generar únicamente la cantidad de recibos correspondiente a su forma de pago.

**⚠️ Pendiente de validación:**

Definir la cantidad exacta de recibos correspondiente a cada forma de pago.

---

### BR-004 — Una póliza tiene un único asegurado

**Descripción:**  
Cada póliza puede tener asociado únicamente un asegurado.

**Aplica a:**

- Póliza
- Asegurado

**Resultado esperado:**

No debe ser posible asociar más de un asegurado a una misma póliza.

---

### BR-005 — Una póliza de vehículo asegura un único vehículo

**Descripción:**  
Cada póliza correspondiente al ramo de vehículos puede asegurar únicamente un vehículo.

**Aplica a:**

- Póliza
- Vehículo

**Resultado esperado:**

Una póliza de vehículo no puede tener asociados múltiples vehículos.

---

### BR-006 — Las pólizas con descuento por nómina no generan recibos

**Descripción:**  
Cuando la forma de pago de una póliza sea descuento por nómina, la póliza no debe tener recibos asociados.

**Aplica a:**

- Póliza
- Recibo
- Forma de pago

**Condición:**

```text
forma_pago = DESCUENTO_POR_NÓMINA
```

**Resultado esperado:**

La póliza debe tener cero recibos asociados.

---

### BR-007 — Una póliza con descuento por nómina se considera en pago al entregar la carta firmada

**Descripción:**  
Una póliza cuya forma de pago sea descuento por nómina se considera en proceso de pago cuando se entrega la carta correspondiente debidamente firmada.

**Aplica a:**

- Póliza
- Forma de pago
- Carta de descuento

**Disparador:**

Recepción o entrega de la carta de descuento firmada.

**Resultado esperado:**

La póliza debe considerarse en estado de pago según el proceso definido por el negocio.

**⚠️ Pendiente de validación:**

Definir exactamente qué significa el estado **"en pago"** y cómo se diferencia de una póliza **"pagada"**.

---

### BR-008 — Una póliza puede cancelarse por solicitud del asegurado o falta de pago

**Descripción:**  
La cancelación de una póliza puede producirse por solicitud del asegurado o como consecuencia de falta de pago.

**Aplica a:**

- Póliza
- Asegurado
- Pago

**Disparadores:**

- Solicitud de cancelación del asegurado.
- Incumplimiento de pago.

**Resultado esperado:**

La póliza entra al proceso de cancelación correspondiente.

---

### BR-009 — Una póliza cuya vigencia ha expirado debe considerarse inactiva o vencida

**Descripción:**  
Cuando la fecha final de vigencia de una póliza haya transcurrido, esta no debe considerarse activa.

**Aplica a:**

- Póliza
- Vigencia

**Condición:**

```text
fecha_actual > fecha_fin_vigencia
```

**Resultado esperado:**

La póliza debe tener un estado equivalente a vencida o inactiva.

**⚠️ Pendiente de validación:**

Definir si `VENCIDA` e `INACTIVA` representan el mismo estado o estados distintos.

---

### BR-010 — Una póliza solo puede emitirse con documentación completa

**Descripción:**  
Una póliza únicamente puede emitirse cuando se cuenta con toda la documentación obligatoria.

**Aplica a:**

- Póliza
- Asegurado
- Vehículo
- Documentación

**Documentación requerida actualmente identificada:**

- INE.
- Tarjeta de circulación o factura.

**Resultado esperado:**

Si falta documentación obligatoria, la póliza no debe emitirse.

**⚠️ Pendiente de validación:**

Determinar si los documentos requeridos cambian según el tipo de seguro o producto.

---

### BR-011 — Las pólizas deben renovarse antes de finalizar su vigencia

**Descripción:**  
El proceso de renovación de una póliza debe realizarse antes de que finalice su vigencia actual.

**Aplica a:**

- Póliza
- Renovación

**Condición:**

```text
fecha_renovación < fecha_fin_vigencia
```

**Resultado esperado:**

La renovación debe gestionarse antes del vencimiento de la póliza.

---

### BR-012 — Las pólizas con descuento por nómina requieren información adicional

**Descripción:**  
Cuando una póliza utiliza descuento por nómina como forma de pago, debe registrarse información adicional relacionada con el descuento.

**Aplica a:**

- Póliza
- Forma de pago

**Información adicional identificada:**

- Quincena de inicio del descuento.
- Estado del trámite.

**Resultado esperado:**

La información adicional debe estar disponible para gestionar correctamente el proceso de descuento por nómina.

---

### BR-013 — Una nueva póliza por cancelación previa por falta de pago debe pagarse antes de emitirse

**Descripción:**  
Cuando una póliza anterior del mismo vehículo haya sido cancelada por falta de pago y se pretenda emitir nuevamente una póliza para dicho vehículo, la nueva póliza debe pagarse antes de su emisión.

**Aplica a:**

- Póliza
- Vehículo
- Pago

**Condiciones:**

1. Existe una póliza anterior del mismo vehículo.
2. La póliza anterior fue cancelada por falta de pago.
3. Se solicita una nueva emisión.

**Resultado esperado:**

El pago debe realizarse antes de que la nueva póliza pueda ser emitida.

---

### BR-014 — Una póliza no puede tener más recibos de los permitidos por su forma de pago

**Descripción:**  
La cantidad de recibos asociados a una póliza no puede superar el límite establecido para su forma de pago.

**Aplica a:**

- Póliza
- Recibo
- Forma de pago

**Resultado esperado:**

El sistema debe impedir que se generen recibos adicionales a los permitidos.

**Relacionada con:**

- BR-003
- BR-006

---

### BR-015 — Los gastos de expedición dependen de la cobertura

**Descripción:**  
El importe correspondiente a gastos de expedición debe determinarse según la cobertura contratada.

**Aplica a:**

- Póliza
- Cobertura
- Gastos de expedición

**Resultado esperado:**

El gasto de expedición debe calcularse utilizando las condiciones correspondientes a la cobertura.

**⚠️ Pendiente de validación:**

Definir los gastos de expedición correspondientes a cada cobertura.

---

## Asegurado

### BR-016 — El descuento por nómina para empleados de la Secretaría de Salud requiere información adicional

**Descripción:**  
Cuando el asegurado sea empleado de la Secretaría de Salud y solicite el pago mediante descuento por nómina, deberá proporcionar información laboral adicional.

**Aplica a:**

- Asegurado
- Forma de pago

**Condiciones:**

```text
empleador = SECRETARÍA_DE_SALUD
forma_pago = DESCUENTO_POR_NÓMINA
```

**Información requerida:**

- RFC.
- Lugar de trabajo.
- Número de empleado.
- Tipo de nómina.

**Resultado esperado:**

La información adicional debe registrarse antes de completar el trámite correspondiente.

---

## Agente

### BR-017 — Un agente no puede tener más de un corte de comisiones activo

**Descripción:**  
Cada agente puede tener como máximo un corte de comisiones activo simultáneamente.

**Aplica a:**

- Agente
- Corte de comisión

**Condición:**

```text
cantidad_cortes_activos <= 1
```

**Resultado esperado:**

No debe permitirse crear un nuevo corte activo mientras exista otro corte activo para el mismo agente.

---

### BR-018 — Una póliza activa del agente puede descontarse de su corte de comisiones

**Descripción:**  
Cuando un agente tenga una póliza activa con la aseguradora, el importe correspondiente debe descontarse de su último corte de comisiones activo.

**Aplica a:**

- Agente
- Póliza
- Corte de comisión

**Resultado esperado:**

El descuento debe aplicarse sobre el último corte activo del agente.

**⚠️ Pendiente de validación:**

Definir:

- qué importe se descuenta;
- cuándo se realiza el descuento;
- si aplica a todas las pólizas del agente;
- qué ocurre si no existe un corte activo.

---

### BR-019 — Un agente solo puede consultar las pólizas asociadas a él

**Descripción:**  
Un agente únicamente puede consultar información de las pólizas que tenga asociadas.

**Aplica a:**

- Agente
- Póliza

**Resultado esperado:**

El sistema debe restringir la consulta de pólizas no asociadas al agente.

---

### BR-020 — Un agente solo puede consultar asegurados asociados a él

**Descripción:**  
Un agente únicamente puede consultar los datos de asegurados que estén asociados a pólizas o relaciones bajo su responsabilidad.

**Aplica a:**

- Agente
- Asegurado

**Resultado esperado:**

El sistema debe impedir que un agente consulte información de asegurados que no estén asociados a él.

---

## Recibo

### BR-021 — Un recibo se considera pagado al registrar su pago

**Descripción:**  
Cuando el pago correspondiente a un recibo se registra correctamente, dicho recibo debe considerarse pagado.

**Aplica a:**

- Recibo
- Pago

**Disparador:**

Registro exitoso del pago.

**Resultado esperado:**

```text
estado_recibo = PAGADO
```

---

### BR-022 — La prima de un recibo no puede ser negativa

**Descripción:**  
El importe correspondiente a la prima de un recibo debe ser igual o mayor a cero.

**Aplica a:**

- Recibo
- Prima

**Condición:**

```text
prima >= 0
```

**Resultado esperado:**

El sistema debe rechazar recibos cuya prima sea negativa.

---

### BR-023 — El periodo permitido para pagar un recibo depende de la aseguradora

**Descripción:**  
La posibilidad de pagar un recibo antes o después de su fecha de vigencia depende de las políticas establecidas por cada aseguradora.

**Aplica a:**

- Recibo
- Aseguradora

