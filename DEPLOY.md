# Guía de Despliegue - IAMET Website

## Archivos creados

```
├── Dockerfile           # Build multi-stage de la app
├── docker-compose.yml   # Orquestación de servicios
├── .dockerignore        # Archivos excluidos del build
└── nginx/
    ├── nginx.conf       # Configuración principal de Nginx
    └── conf.d/
        └── iamet.conf   # Configuración del sitio
```

## Pasos para desplegar

### 1. Subir archivos al servidor

```bash
# Opción A: Con rsync
rsync -avz --exclude node_modules --exclude dist ./ usuario@servidor:/ruta/iamet-website/

# Opción B: Con scp
scp -r ./ usuario@servidor:/ruta/iamet-website/

# Opción C: Clonar desde git (si tienes repo)
git clone tu-repo.git /ruta/iamet-website
```

### 2. Configurar dominio

Edita `nginx/conf.d/iamet.conf` y cambia:
```
server_name tudominio.com www.tudominio.com;
```
Por tu dominio real.

### 3. Construir y levantar

```bash
cd /ruta/iamet-website

# Construir imágenes
docker compose build

# Levantar servicios
docker compose up -d

# Ver logs
docker compose logs -f
```

### 4. Verificar que funciona

```bash
# Verificar contenedores
docker compose ps

# Probar localmente
curl http://localhost
```

## Configurar SSL con Let's Encrypt

### Opción A: Usando Certbot en el host

```bash
# Instalar certbot
apt install certbot

# Obtener certificado
certbot certonly --webroot -w /var/www/certbot -d tudominio.com -d www.tudominio.com

# Los certificados quedan en /etc/letsencrypt/live/tudominio.com/
```

### Opción B: Docker con Certbot

Agrega esto a `docker-compose.yml`:

```yaml
  certbot:
    image: certbot/certbot
    volumes:
      - ./certbot/conf:/etc/letsencrypt
      - ./certbot/www:/var/www/certbot
    command: certonly --webroot -w /var/www/certbot -d tudominio.com --email tu@email.com --agree-tos
```

### Activar HTTPS

1. Edita `nginx/conf.d/iamet.conf`
2. Descomenta el bloque `server` con `listen 443 ssl`
3. Descomenta la redirección HTTP->HTTPS
4. Actualiza las rutas de certificados
5. Reinicia: `docker compose restart nginx`

## Comandos útiles

```bash
# Reconstruir después de cambios
docker compose build --no-cache
docker compose up -d

# Ver logs en tiempo real
docker compose logs -f iamet-web
docker compose logs -f nginx

# Reiniciar un servicio
docker compose restart iamet-web

# Parar todo
docker compose down

# Parar y eliminar volúmenes
docker compose down -v

# Ver uso de recursos
docker stats
```

## Integración con Nginx existente en el servidor

Si ya tienes Nginx corriendo en tu servidor (no en Docker), puedes:

### Opción 1: Usar solo el contenedor de la app

Modifica `docker-compose.yml`:
```yaml
services:
  iamet-web:
    build: .
    ports:
      - "3000:3000"  # Exponer puerto directamente
    restart: unless-stopped
```

Y en tu Nginx del servidor, agrega un site:
```nginx
server {
    listen 80;
    server_name tudominio.com;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

### Opción 2: Red Docker compartida

Si tienes otros servicios en Docker con una red compartida:
```yaml
networks:
  iamet-network:
    external: true
    name: mi-red-compartida
```

## Troubleshooting

**Error: puerto 80 ya en uso**
```bash
# Ver qué usa el puerto
sudo lsof -i :80
# O parar nginx del host
sudo systemctl stop nginx
```

**Error: permisos de archivos**
```bash
# Dar permisos
chmod -R 755 /ruta/iamet-website
```

**App no inicia**
```bash
# Ver logs detallados
docker compose logs iamet-web
# Entrar al contenedor
docker compose exec iamet-web sh
```
