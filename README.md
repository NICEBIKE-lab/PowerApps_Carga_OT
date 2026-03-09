# PowerApps_Carga_OT

Actúa como **arquitecto de software senior especializado en documentación de arquitectura y diseño de integraciones API**.

Tu tarea es generar **documentación técnica completa y estructurada** para una solución de integración que automatiza la creación de órdenes de trabajo en Fracttal a partir de registros almacenados en SharePoint Lists, usando Power Automate para la orquestación.

Utiliza únicamente **información verificable y buenas prácticas de arquitectura**.
No inventes campos de API ni estructuras que no estén documentadas.

---

# 1. Contexto del sistema

La solución implementa un flujo automatizado donde:

1. Los usuarios registran solicitudes o tareas en una lista de SharePoint.
2. Un flujo de Power Automate detecta nuevos registros.
3. El flujo ejecuta una llamada HTTP a la API de Fracttal.
4. Se crea una orden de trabajo en Fracttal.
5. El identificador o folio de la OT se guarda nuevamente en la lista de SharePoint para trazabilidad.

Tecnologías involucradas:

* Microsoft SharePoint Lists (almacenamiento de registros)
* Microsoft Power Automate (automatización de flujos)
* API REST de Fracttal (creación de órdenes de trabajo)
* Autenticación mediante token API

Endpoints relevantes:

POST /api/work_orders/
GET /api/work_orders/{folio}

---

# 2. Entregables requeridos

Genera la documentación en las siguientes secciones.

---

# A. Arquitectura usando modelo C4

Generar los siguientes diagramas:

### 1. Diagrama de Contexto (C4 Level 1)

Debe mostrar:

* Usuario / operador de mantenimiento
* Sistema de gestión de mantenimiento Fracttal
* SharePoint Lists
* Power Automate

Explicar las relaciones entre sistemas.

---

### 2. Diagrama de Contenedores (C4 Level 2)

Describir:

* Lista SharePoint como almacenamiento de datos
* Flujo de Power Automate como motor de integración
* API REST de Fracttal
* Sistema Fracttal CMMS

Mostrar protocolos usados:

* HTTPS
* REST API

---

### 3. Diagrama de Componentes (C4 Level 3)

Componentes dentro del flujo de automatización:

* Trigger de creación de registro
* Acción HTTP
* Procesamiento de respuesta
* Persistencia del folio OT

---

# B. Diagramas de Secuencia

Crear diagramas de secuencia que describan el flujo completo.

### Escenario principal

1. Usuario crea registro en SharePoint
2. Power Automate detecta evento
3. Power Automate llama API Fracttal
4. Fracttal crea OT
5. API devuelve folio
6. Power Automate actualiza SharePoint

---

### Escenario de error

1. API devuelve error HTTP
2. Flujo registra error
3. Se notifica al administrador

---

# C. Architecture Decision Records (ADR)

Generar ADR documentando decisiones clave:

### ADR-001

Uso de SharePoint Lists como repositorio de solicitudes.

### ADR-002

Uso de Power Automate para integración sin código.

### ADR-003

Creación de órdenes de trabajo mediante API REST de Fracttal.

Cada ADR debe incluir:

* Contexto
* Decisión
* Consecuencias
* Alternativas consideradas

---

# D. Especificación de Integración (tipo OpenAPI simplificado)

Documentar la interacción con la API.

Incluir:

### Endpoint

POST /api/work_orders/

### Headers requeridos

Authorization: Bearer API_TOKEN
Content-Type: application/json

### Ejemplo de Request

JSON representativo basado en documentación oficial.

### Ejemplo de Response

Estructura que incluya identificador o folio de la OT.

---

# E. Manejo de errores

Documentar posibles errores:

400 Bad Request
401 Unauthorized
404 Not Found
500 Server Error

Explicar cómo el flujo debe gestionarlos.

---

# F. Observabilidad y monitoreo

Documentar:

* logs del flujo
* almacenamiento del folio OT
* trazabilidad entre SharePoint y Fracttal

---

# G. Consideraciones de escalabilidad

Explicar:

* límites de llamadas API
* procesamiento masivo
* control de concurrencia en flujos

---

# 3. Formato de salida esperado

La documentación debe incluir:

* diagramas en formato Mermaid o PlantUML
* ejemplos JSON
* secciones claras con encabezados
* lenguaje técnico de arquitectura
* estructura similar a documentación de arquitectura empresarial
