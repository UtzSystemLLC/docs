
# Proyecto

Bienvenido a la documentación del proyecto. Usa los enlaces a continuación para navegar:

- [Configuración SSH](ssh.md)
- [Documentación de Swagger](swagger.md)
- [Documentación de Go](go.md)
- [Documentación de Nginx](nginx.md)
- [Configuración Nginx - React](config-nginx.md)

## Ejecutar una aplicación React en segundo plano

Si tienes una aplicación React compilada en un directorio `dist` o `build` y deseas ejecutarla en segundo plano, puedes usar un servidor como `serve` o `http-server`.

### 1. Instalar un servidor estático

Si aún no tienes un servidor instalado, puedes usar `serve` (recomendado):

```bash
npm install -g serve
```

### 2. Ejecutar la aplicación en segundo plano

Usa el siguiente comando para servir tu aplicación React en segundo plano:

```bash
nohup serve -s build -l 3000 > react-app.log 2>&1 &
```

- **`serve -s build`**: Sirve el contenido del directorio `build` de React como una SPA (Single Page Application).
- **`-l 3000`**: Define el puerto (puedes cambiarlo si es necesario).
- **`nohup` y `&`**: Ejecutan el comando en segundo plano.
- **`> react-app.log 2>&1`**: Redirige la salida estándar y los errores al archivo `react-app.log`.

### 3. Buscar el proceso

Para encontrar el proceso que ejecuta el servidor React:

```bash
pgrep -fl serve
```

Esto mostrará algo como:

```
67890 serve -s build -l 3000
```

### 4. Detener el proceso

Para detener el servidor React, usa el comando `kill` con el PID del proceso:

```bash
kill 67890
```

Si es necesario, usa `kill -9` para forzar su detención:

```bash
kill -9 67890
```

