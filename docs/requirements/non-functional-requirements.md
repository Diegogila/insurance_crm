# Non-Functional Requirements

## Requisitos

### NFR-001 — Disponibilidad

**Categoría:** Disponibilidad

**Requisito:**  
El sistema debe estar disponible para los usuarios autorizados fuera del horario habitual de oficina, sin depender de que las instalaciones físicas de la organización se encuentren abiertas.

**Criterio de verificación:**  
Un usuario autorizado debe poder acceder al sistema y utilizar sus funcionalidades disponibles fuera del horario habitual de oficina, siempre que disponga de conexión y no exista una interrupción planificada del servicio.

**Justificación:**  
La gestión de pólizas y consultas puede requerirse fuera del horario habitual de operación de la oficina.

---

### NFR-002 — Accesibilidad multicanal

**Categoría:** Usabilidad / Accesibilidad

**Requisito:**  
El sistema debe permitir el acceso a sus funcionalidades desde más de un canal de acceso compatible.

**Criterio de verificación:**  
Las funcionalidades principales del sistema deben poder utilizarse correctamente desde, al menos, dos canales de acceso definidos como compatibles por el proyecto.

**Justificación:**  
Los usuarios pueden necesitar acceder al sistema desde diferentes medios dependiendo de su ubicación y contexto de trabajo.

---

### NFR-003 — Protección de la información

**Categoría:** Seguridad

**Requisito:**  
El sistema debe proteger la información gestionada, especialmente los datos personales, financieros y demás información considerada sensible dentro del dominio.

**Criterio de verificación:**  
El acceso a información sensible debe estar restringido a usuarios autorizados y las operaciones sobre dicha información deben respetar los mecanismos de seguridad definidos por el sistema.

**Justificación:**  
El negocio gestiona información de clientes, pólizas y operaciones que puede contener datos sensibles y requiere protección frente a accesos no autorizados.