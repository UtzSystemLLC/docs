# Instalación de Go 1.23.4 en Ubuntu

Este documento describe los pasos necesarios para instalar Go 1.23.4 en un sistema Ubuntu.

---

## 1. Descargar la versión específica de Go
Descarga el archivo tar.gz correspondiente a la versión 1.23.4 de Go desde el sitio oficial o utilizando `wget`:

```bash
wget https://go.dev/dl/go1.23.4.linux-amd64.tar.gz
```

---

## 2. Eliminar cualquier versión anterior de Go
Si tienes una versión previa de Go instalada, elimínala para evitar conflictos:

```bash
sudo rm -rf /usr/local/go
```

---

## 3. Extraer el archivo descargado
Extrae el archivo tar.gz en el directorio `/usr/local`, que es el recomendado para instalar Go:

```bash
sudo tar -C /usr/local -xzf go1.23.4.linux-amd64.tar.gz
```

---

## 4. Configurar las variables de entorno
Agrega Go al `PATH` para que el sistema reconozca el comando `go` desde cualquier terminal:

1. Edita el archivo `~/.profile` o `~/.bashrc` (elige uno según tu configuración):

   ```bash
   nano ~/.profile
   ```

2. Agrega las siguientes líneas al final del archivo:

   ```bash
   export PATH=$PATH:/usr/local/go/bin
   ```

3. Aplica los cambios ejecutando:

   ```bash
   source ~/.profile
   ```

---

## 5. Verificar la instalación
Verifica que Go se haya instalado correctamente y que estás usando la versión 1.23.4:

```bash
go version
```
---

## 6. Configurar tu espacio de trabajo (opcional)
Por defecto, el espacio de trabajo de Go se encuentra en `~/go`. Si prefieres cambiarlo, puedes establecer la variable `GOPATH`:

1. Edita el archivo `~/.profile` o `~/.bashrc` nuevamente:

   ```bash
   nano ~/.profile
   ```

2. Agrega las siguientes líneas:

   ```bash
   export GOPATH=$HOME/my-go-workspace
   export PATH=$PATH:$GOPATH/bin
   ```

3. Aplica los cambios:

   ```bash
   source ~/.profile
   ```

---

## Ejecutar un programa Go en segundo plano

Si deseas ejecutar un programa Go en segundo plano y gestionarlo fácilmente, sigue estos pasos:

### 1. Ejecutar el programa en segundo plano

Usa el siguiente comando para ejecutar el programa `main.go` en segundo plano:

```bash
nohup go run main.go &
```

- **`nohup`**: Ignora las señales de "hangup" para que el proceso continúe incluso si cierras la terminal.
- **`&`**: Coloca el proceso en segundo plano.

Si deseas redirigir la salida a un archivo específico:

```bash
nohup go run main.go > output.log 2>&1 &
```

Esto enviará tanto la salida estándar como los errores al archivo `output.log`.

### 2. Buscar el proceso

Para encontrar el proceso en ejecución, usa el comando `pgrep`:

```bash
pgrep -fl main
```

- **`pgrep`**: Busca procesos por nombre.
- **`-f`**: Busca en el comando completo.
- **`-l`**: Muestra los nombres de los procesos junto con sus PIDs (Process IDs).

El comando devolverá algo como:

```
12345 go run main.go
```

Donde `12345` es el PID del proceso.

### 3. Detener el proceso

Para detener el proceso, usa el comando `kill` seguido del PID:

```bash
kill 12345
```

Si el proceso no responde, puedes forzar su detención con:

```bash
kill -9 12345
```

---

Con estos pasos, puedes ejecutar tu programa Go en segundo plano, buscarlo fácilmente y detenerlo cuando sea necesario.

---