# WhatsApp

Configuración NGINX
```bash
# En la configuración de nginx se agrega el puerto al final cuando no se usa el puerto 443 por default
sudo nano /etc/nginx/sites-available/mia.chanim.com.gt-3005

# Habilitarlo
sudo ln -s /etc/nginx/sites-available/mia.chanim.com.gt-3005 /etc/nginx/sites-enabled/

# Validar
sudo nginx -t

# Reiniciar servicio
sudo systemctl reload nginx
```


| Caso                           | Archivo NGINX                                     | Para qué sirve                                                                 |
| ------------------------------ | ------------------------------------------------- | ------------------------------------------------------------------------------ |
| Solo pruebas en puerto 3005    | /etc/nginx/sites-available/mia.chanim.com.gt-3005 | Acceso por [https://mia.chanim.com.gt:3005](https://mia.chanim.com.gt:3005)    |
| Producción real (443 estándar) | /etc/nginx/sites-available/mia.chanim.com.gt      | Acceso por [https://mia.chanim.com.gt](https://mia.chanim.com.gt) (sin puerto) |


 ¿Cómo ver qué sitios activos tiene NGINX?
 ```bash
# Los sitios activos son simplemente los archivos enlazados en:
cd /etc/nginx/sites-enabled/
ls

# Este directorio contiene enlaces simbólicos (symlinks) que apuntan a los archivos reales en:
cd /etc/nginx/sites-available/
ls

# 🛠 Comando para listarlos
ls -l /etc/nginx/sites-enabled/
```

🛠 Si quieres ver toda la configuración consolidada que NGINX ha cargado:
```bash
sudo nginx -T
```


🔧 Si quieres desactivar un sitio
Simplemente elimina el enlace simbólico:
```bash
sudo rm /etc/nginx/sites-enabled/mia.chanim.com.gt-3005
sudo systemctl reload nginx
```