# Infrastructure AI Agent - Templates Repository

Este repositorio contiene los archivos YAML generados automáticamente por el AI Agent para el catálogo de Backstage.

## Estructura

```
├── components/     # Componentes de aplicaciones
├── resources/      # Recursos de infraestructura  
├── systems/        # Sistemas completos
└── README.md       # Esta documentación
```

## Uso

Los archivos YAML se generan automáticamente cuando:

1. Se envía un diagrama o descripción al AI Agent
2. El agente procesa con Gemini AI
3. Se genera YAML válido para Backstage
4. Se hace commit automático a este repositorio
5. Backstage detecta los cambios y actualiza el catálogo

## Integración con Backstage

Este repositorio está configurado en Backstage para:
- Monitoreo automático de cambios
- Importación de nuevos componentes
- Actualización del catálogo cada 5 minutos

## AI Agent

- **Repositorio**: https://github.com/giovanemere/demo-infra-ai-agent
- **API**: http://localhost:8000
- **Docs**: http://localhost:8000/docs
