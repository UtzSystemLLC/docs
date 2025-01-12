
## Instalación y uso de Swag para documentación Swagger en Go

Si deseas usar Swag para generar documentación Swagger en tu proyecto Go, sigue estos pasos:

### 1. Instalar `swag`

Ejecuta el siguiente comando para instalar la herramienta `swag`:

```bash
go install github.com/swaggo/swag/cmd/swag@latest
```

Esto descargará e instalará el ejecutable de `swag` en el directorio `$GOPATH/bin`.

### 2. Configurar el `PATH`

Asegúrate de que `$GOPATH/bin` esté incluido en tu variable `PATH`. Para hacerlo, edita el archivo `~/.profile` o `~/.bashrc` y agrega:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```

Luego aplica los cambios ejecutando:

```bash
source ~/.profile
```

### 3. Verificar la instalación

Confirma que `swag` se instaló correctamente ejecutando:

```bash
swag --version
```

Deberías ver la versión de `swag` si todo está configurado correctamente.

### 4. Generar documentación Swagger en tu proyecto

Navega al directorio de tu proyecto Go y ejecuta:

```bash
swag init
```

Esto generará los archivos necesarios (`docs`) para la documentación Swagger.

### 5. Incluir la documentación en tu proyecto

En tu código Go, importa y configura la documentación generada para exponerla a través de un endpoint (por ejemplo, `/swagger/index.html`).

### ¡Todo listo!
Con estos pasos, Swag estará instalado y listo para generar documentación Swagger para tu proyecto Go.


---
