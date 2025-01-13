# Gestión del Proyecto con PM2

Este documento describe cómo manejar el proyecto utilizando **PM2**, asignándole el nombre `frontend` y ejecutando el script `npm run dist`.

## Comandos Básicos

### 1. Iniciar el Proyecto
Para iniciar el proyecto y asignarle el nombre `frontend`:
```bash
pm2 start npm --name "frontend" -- run dist
```

### 2. Listar Procesos en Ejecución
Para ver los procesos gestionados por PM2:
```bash
pm2 list
```

### 3. Detener el Proyecto
Para detener el proyecto llamado `frontend`:
```bash
pm2 stop frontend
```

### 4. Reiniciar el Proyecto
Para reiniciar el proyecto llamado `frontend`:
```bash
pm2 restart frontend
```

### 5. Ver Logs del Proyecto
Para ver los logs del proyecto en tiempo real:
```bash
pm2 logs frontend
```

### 6. Eliminar el Proyecto de PM2
Para eliminar el proyecto de la gestión de PM2:
```bash
pm2 delete frontend
```

### 7. Guardar la Configuración Actual
Para guardar la configuración actual, de manera que los procesos se reinicien automáticamente tras un reinicio del servidor:
```bash
pm2 save
```

### 8. Cargar la Configuración Guardada
Para cargar la configuración guardada después de un reinicio del servidor:
```bash
pm2 resurrect
```

### 9. Monitorizar el Estado del Proyecto
Para monitorizar el estado y el rendimiento del proyecto:
```bash
pm2 monit
```

## Notas
- Asegúrate de que PM2 esté instalado globalmente en tu sistema antes de usar estos comandos. Puedes instalarlo con:
  ```bash
  npm install -g pm2
  ```

- Si necesitas más información sobre PM2, consulta la [documentación oficial](https://pm2.keymetrics.io/).
