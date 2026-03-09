# PowerApps_Carga_OT

Solución de integración que automatiza la creación de **Órdenes de Trabajo (OT)** en Fracttal CMMS a partir de registros almacenados en SharePoint Lists, orquestada mediante Microsoft Power Automate.

## Flujo general

```
Usuario → SharePoint List → Power Automate → API REST Fracttal → OT creada → SharePoint actualizado
```

## Documentación técnica

La documentación de arquitectura completa se encuentra en:

📄 **[docs/arquitectura-integracion.md](docs/arquitectura-integracion.md)**

Incluye:

- **Arquitectura C4** — Diagramas de Contexto, Contenedores y Componentes
- **Diagramas de Secuencia** — Flujo exitoso y escenario de error
- **Architecture Decision Records (ADR)** — ADR-001, ADR-002, ADR-003
- **Especificación de integración API** — Endpoints, headers, ejemplos JSON
- **Manejo de errores** — Estrategias por código HTTP (400, 401, 404, 429, 500, 503)
- **Observabilidad y monitoreo** — Logs, trazabilidad, alertas
- **Consideraciones de escalabilidad** — Límites, procesamiento masivo, concurrencia

## Tecnologías

| Componente | Tecnología |
|---|---|
| Almacenamiento de solicitudes | Microsoft SharePoint Lists |
| Motor de integración | Microsoft Power Automate |
| Sistema CMMS | Fracttal |
| Protocolo de integración | REST / HTTPS |
| Autenticación | Bearer Token (API Key) |
