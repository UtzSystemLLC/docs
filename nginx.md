# Comandos y Configuración Básica de Nginx

## **1. Iniciar, Detener y Reiniciar Nginx**

### Iniciar Nginx:
```bash
sudo systemctl start nginx
```

### Detener Nginx:
```bash
sudo systemctl stop nginx
```

### Reiniciar Nginx:
```bash
sudo systemctl restart nginx
```

### Recargar Configuración sin Detener el Servicio:
```bash
sudo systemctl reload nginx
```

## **2. Verificar el Estado del Servicio Nginx**

### Estado del Servicio:
```bash
sudo systemctl status nginx
```

## **3. Validar la Configuración de Nginx**

### Probar la Configuración para Errores de Sintaxis:
```bash
sudo nginx -t
```

## **4. Logs**

### Ver Logs de Acceso:
```bash
tail -f /var/log/nginx/access.log
```

### Ver Logs de Errores:
```bash
tail -f /var/log/nginx/error.log
```

## **5. Control Manual de Nginx**

### Iniciar Nginx Manualmente:
```bash
sudo nginx
```

### Detener Nginx Manualmente:
```bash
sudo nginx -s stop
```

### Recargar Configuración Manualmente:
```bash
sudo nginx -s reload
```

## **6. Comandos Avanzados de Configuración**

### Listar Módulos Compilados:
```bash
nginx -V 2>&1 | grep -- '--with'
```

### Editar el Archivo de Configuración Principal:
```bash
sudo nano /etc/nginx/nginx.conf
```

## **7. Estructura de Directorios de Nginx**

- **Archivo de Configuración Principal:**
  ```bash
  /etc/nginx/nginx.conf
  ```

- **Sitios Disponibles:**
  ```bash
  /etc/nginx/sites-available/
  ```

- **Sitios Habilitados:**
  ```bash
  /etc/nginx/sites-enabled/
  ```

## **8. Habilitar y Deshabilitar Sitios**

### Habilitar un Sitio:
```bash
sudo ln -s /etc/nginx/sites-available/nombredelsitio.conf /etc/nginx/sites-enabled/
```

### Deshabilitar un Sitio:
```bash
sudo rm /etc/nginx/sites-enabled/nombredelsitio.conf
```

## **9. Mejores Prácticas para Cambios en la Configuración**

1. **Validar la Configuración:**
   ```bash
   sudo nginx -t
   ```
2. **Recargar el Servicio:**
   ```bash
   sudo systemctl reload nginx
   ```

## **10. Consejos Útiles**

- Siempre realiza una copia de seguridad de los archivos de configuración antes de hacer cambios.
- Usa `sudo nginx -t` para detectar errores de sintaxis rápidamente.
- Para depurar problemas, revisa los logs ubicados en `/var/log/nginx/`.

## **Resolución de Problemas**

Si Nginx falla al iniciar o recargar, verifica:
1. **Logs de Errores:**
   ```bash
   sudo tail -f /var/log/nginx/error.log
   ```
2. **Estado del Servicio:**
   ```bash
   sudo systemctl status nginx
   ```

# Configuración WhatsApp NGINX
```bash
server {
    listen 3005 ssl;
    server_name mia.chanim.com.gt;

    ssl_certificate /home/ubuntu/ssl/mia.chanim.com.gt.pem;
    ssl_certificate_key /home/ubuntu/ssl/mia.chanim.com.gt.key;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;

    # /webhook → proxy al backend Express
    location /webhook {
        proxy_pass http://127.0.0.1:3006/webhook;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    # / (raíz) → proxy al backend Express
    location / {
        proxy_pass http://127.0.0.1:3006/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```