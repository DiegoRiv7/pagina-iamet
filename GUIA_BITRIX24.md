# Guía de Integración con Bitrix24

Esta guía explica cómo conectar el sitio web de IAMET con Bitrix24 para capturar leads y gestionar solicitudes de soporte.

## Archivo de Configuración

Todos los placeholders de integración se encuentran en:

```
client/src/lib/config.ts
```

## 1. Formularios Web de Bitrix24 (Embed)

### Formulario de Ventas/Diagnóstico

1. En Bitrix24, vaya a **CRM > Formularios web**
2. Cree un nuevo formulario o edite uno existente para captación de leads
3. Configure los campos:
   - Nombre completo
   - Empresa
   - Email
   - Teléfono
   - Servicio de interés (lista)
   - Mensaje
4. En la pestaña "Publicar", copie el código de inserción
5. En `config.ts`, reemplace:

```typescript
export const BITRIX_WEBFORM_SCRIPT_VENTAS = "PEGAR_AQUI";
```

Por el código copiado de Bitrix24, por ejemplo:

```typescript
export const BITRIX_WEBFORM_SCRIPT_VENTAS = `<script data-b24-form="inline/XX/XXXXX" data-skip-moving="true">(function(w,d,u){var s=d.createElement('script');s.async=true;s.src=u+'?'+(Date.now()/180000|0);var h=d.getElementsByTagName('script')[0];h.parentNode.insertBefore(s,h);})(window,document,'https://sudominio.bitrix24.com/upload/crm/form/loader_XX.js');</script>`;
```

### Formulario de Servicio/Soporte

Repita el proceso anterior para el formulario de soporte:

```typescript
export const BITRIX_WEBFORM_SCRIPT_SERVICIO = "PEGAR_AQUI";
```

## 2. REST Webhook de Bitrix24

Si prefiere enviar datos mediante API en lugar de formularios embed:

### Crear el Webhook

1. En Bitrix24, vaya a **Aplicaciones > Webhooks**
2. Haga clic en "Añadir webhook" > "Webhook entrante"
3. Asigne un nombre descriptivo (ej: "Web IAMET")
4. Seleccione los permisos necesarios:
   - `crm` - Para crear leads y negocios
5. Copie la URL generada

### Configurar en el sitio

En `config.ts`, reemplace:

```typescript
export const BITRIX_WEBHOOK_URL = "PEGAR_AQUI";
```

Por la URL del webhook, por ejemplo:

```typescript
export const BITRIX_WEBHOOK_URL = "https://sudominio.bitrix24.com/rest/1/abc123xyz/";
```

### Métodos disponibles

El sitio está preparado para usar estos métodos:

| Método | Descripción |
|--------|-------------|
| `crm.lead.add` | Crear nuevo lead (usado por defecto) |
| `crm.deal.add` | Crear nuevo negocio |
| `crm.contact.add` | Crear nuevo contacto |

### Campos enviados

El formulario de ventas envía:

```json
{
  "TITLE": "Lead Web - [Empresa]",
  "NAME": "[Nombre completo]",
  "COMPANY_TITLE": "[Empresa]",
  "EMAIL": [{ "VALUE": "[Email]", "VALUE_TYPE": "WORK" }],
  "PHONE": [{ "VALUE": "[Teléfono]", "VALUE_TYPE": "WORK" }],
  "SOURCE_ID": "WEB",
  "COMMENTS": "Servicio de interés: [Servicio]\n\nMensaje: [Mensaje]"
}
```

## 3. Widget de Live Chat

### Configurar el widget

1. En Bitrix24, vaya a **Contact Center > Widget del sitio web**
2. Configure el widget de chat en vivo según sus preferencias
3. En la pestaña "Código", copie el script de inserción
4. En `config.ts`, reemplace:

```typescript
export const BITRIX_LIVECHAT_WIDGET_SCRIPT = "PEGAR_AQUI";
```

### Integración con el asistente

El asistente virtual (ChatBot) del sitio detectará automáticamente si hay un widget de Bitrix24 configurado y abrirá el chat cuando el usuario seleccione una opción.

## 4. Información de Contacto

Actualice la información de contacto en `config.ts`:

```typescript
export const CONTACT_INFO = {
  email: "contacto@iamet.com.mx",
  phone: "+52 (55) 1234-5678",
  phoneDisplay: "(55) 1234-5678",
  address: "Av. Insurgentes Sur 1234, Col. Del Valle, CDMX, México, CP 03100",
  addressShort: "Col. Del Valle, CDMX",
  schedule: "Lunes a Viernes: 9:00 - 18:00",
  emergencyPhone: "+52 (55) 9876-5432",
};
```

## 5. Redes Sociales

Configure los enlaces a redes sociales:

```typescript
export const SOCIAL_LINKS = {
  linkedin: "https://linkedin.com/company/iamet",
  facebook: "https://facebook.com/iametmx",
  twitter: "https://twitter.com/iametmx",
};
```

## Verificación

Después de configurar las integraciones:

1. **Pruebe el formulario de ventas**: Complete el formulario y verifique que el lead aparezca en Bitrix24 CRM
2. **Pruebe el formulario de soporte**: Envíe una solicitud y confirme la creación del ticket
3. **Pruebe el chat**: Si configuró Live Chat, verifique que el widget aparezca y funcione correctamente

## Solución de Problemas

### El formulario no envía datos

- Verifique que la URL del webhook sea correcta
- Confirme que el webhook tenga permisos de CRM
- Revise la consola del navegador para errores

### El widget de chat no aparece

- Asegúrese de que el script esté correctamente pegado
- Verifique que no haya bloqueadores de scripts activos
- Confirme que el widget esté activo en Bitrix24

### Los campos no se mapean correctamente

- Revise la estructura de campos en `config.ts`
- Verifique que los campos personalizados existan en Bitrix24
- Consulte la documentación de la API de Bitrix24

## Soporte

Para asistencia adicional con la integración, contacte al equipo de desarrollo de IAMET.
