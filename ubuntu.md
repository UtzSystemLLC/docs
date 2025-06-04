
# Ubuntu

Comprobar si el puerto 3006 se esta ejecuntando

```bash
# Linux & MacOS
sudo lsof -i :3006

# Windows
netstat -ano | findstr :3006
```