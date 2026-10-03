# Functional Requirements

## Requisitos

### FR-001 — Consultar información de una póliza

**Descripción:**  
El sistema debe permitir consultar la información asociada a una póliza registrada.

**Resultado esperado:**  
El usuario autorizado puede visualizar la información disponible de la póliza seleccionada.

**Relacionado con:**

- Póliza

---

### FR-002 — Modificar registros

**Descripción:**  
El sistema debe permitir modificar la información de los registros que sean editables dentro del sistema.

**Resultado esperado:**  
Los cambios realizados deben actualizar la información correspondiente del registro.

**Pendiente de definición:**

Determinar qué tipos de registros pueden modificarse y qué campos deben permanecer restringidos.

---

### FR-003 — Filtrar registros

**Descripción:**  
El sistema debe permitir filtrar los registros disponibles mediante criterios de búsqueda.

**Resultado esperado:**  
El usuario debe poder obtener únicamente los registros que coincidan con los criterios seleccionados.

**Pendiente de definición:**

Determinar los criterios de filtrado disponibles para cada tipo de registro.

---

### FR-004 — Realizar cálculos automáticos

**Descripción:**  
El sistema debe realizar automáticamente los cálculos necesarios para determinados valores del negocio, como comisiones y primas.

**Resultado esperado:**  
Los valores calculados deben generarse utilizando las reglas de negocio correspondientes.

**Relacionado con:**

- Comisión
- Prima
- Reglas de negocio de cálculo

**Pendiente de definición:**

Identificar todos los cálculos que deberán automatizarse y las reglas específicas aplicables a cada uno.

---

### FR-005 — Actualizar estados de registros

**Descripción:**  
El sistema debe permitir actualizar el estado de los registros cuando ocurra un evento o condición que requiera dicho cambio.

**Resultado esperado:**  
El registro debe reflejar su estado actual de acuerdo con las reglas del negocio.

**Relacionado con:**

- Póliza
- Recibo
- Comisión
- Otros registros con ciclo de vida

**Pendiente de definición:**

Determinar qué estados pueden actualizarse manualmente y cuáles deben actualizarse automáticamente.

---

### FR-006 — Notificar cambios críticos en una póliza

**Descripción:**  
El sistema debe notificar los cambios de estado considerados críticos en una póliza.

**Resultado esperado:**  
Los usuarios correspondientes deben recibir una notificación cuando ocurra un cambio crítico.

**Relacionado con:**

- Póliza
- Notificaciones

**Pendiente de definición:**

Determinar:

- qué cambios de estado se consideran críticos;
- quién debe recibir cada notificación;
- qué medio de notificación debe utilizarse.

---

### FR-007 — Consultar información de la aseguradora

**Descripción:**  
El sistema debe poder solicitar información proveniente de la aseguradora para incorporarla al sistema cuando sea necesario.

**Resultado esperado:**  
La información obtenida debe poder utilizarse o registrarse dentro del sistema según el proceso correspondiente.

**Relacionado con:**

- Aseguradora
- Póliza

**Pendiente de definición:**

Determinar:

- qué información se solicitará;
- mediante qué mecanismo se obtendrá;
- con qué frecuencia se realizará la consulta.

---

### FR-008 — Consultar información de la institución financiera

**Descripción:**  
El sistema debe poder solicitar información relacionada con pagos proveniente de una institución financiera para su registro y procesamiento.

**Resultado esperado:**  
La información recibida debe poder asociarse con los registros correspondientes dentro del sistema.

**Relacionado con:**

- Pago
- Recibo
- Institución financiera

**Pendiente de definición:**

Determinar:

- qué información de pagos se consultará;
- cómo se identificarán los pagos;
- mediante qué mecanismo se obtendrá la información.

---

### FR-009 — Enviar información a sistemas externos

**Descripción:**  
El sistema debe permitir enviar información o archivos a actores o sistemas externos cuando un proceso del negocio lo requiera.

**Destinos actualmente identificados:**

- Aseguradora
- Institución financiera

**Resultado esperado:**  
La información debe enviarse al destino correspondiente en el formato requerido por el proceso.

**Pendiente de definición:**

Determinar:

- qué información o archivos deben enviarse;
- qué destinos externos participan;
- qué formato requiere cada destino;
- mediante qué mecanismo se realizará el envío.

---