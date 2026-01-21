# ${{ values.name | title }}

## 📋 Descripción
${{ values.description }}

## 🏗️ Arquitectura AWS

### Servicios Utilizados
- **Amazon S3**: Almacenamiento de archivos estáticos (HTML, CSS, JS)
- **Amazon CloudFront**: CDN para distribución global de contenido

### Configuración
- **Región AWS**: ${{ values.aws_region }}
- **Ambiente**: ${{ values.environment }}
{% if values.domain_name %}
- **Dominio**: ${{ values.domain_name }}
{% endif %}

## 🚀 Despliegue

### Prerrequisitos
- AWS CLI configurado
- Credenciales AWS con permisos para S3 y CloudFront
- Dominio configurado (opcional)

### Pasos de Despliegue
1. **Crear bucket S3**:
   ```bash
   aws s3 mb s3://${{ values.name }}-${{ values.environment }} --region ${{ values.aws_region }}
   ```

2. **Configurar bucket para hosting**:
   ```bash
   aws s3 website s3://${{ values.name }}-${{ values.environment }} \
     --index-document index.html \
     --error-document error.html
   ```

3. **Subir archivos**:
   ```bash
   aws s3 sync ./dist/ s3://${{ values.name }}-${{ values.environment }} --delete
   ```

4. **Crear distribución CloudFront**:
   ```bash
   aws cloudfront create-distribution \
     --distribution-config file://cloudfront-config.json
   ```

## 📊 Monitoreo
- **CloudWatch**: Métricas de S3 y CloudFront
- **AWS Console**: [S3 Console](https://console.aws.amazon.com/s3/)
- **CloudFront Console**: [CloudFront Console](https://console.aws.amazon.com/cloudfront/)

## 🔗 Enlaces
- [Repositorio](https://github.com/giovanemere/${{ values.name }})
- [AWS Console](https://console.aws.amazon.com/)
- [Backstage Catalog](http://localhost:3000/catalog/default/component/${{ values.name }})

---
*Generado automáticamente por Infrastructure AI Platform*
