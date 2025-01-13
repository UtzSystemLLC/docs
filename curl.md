# Curl

```bash
# peticiones al backend con localhost para validar la configuración
curl -X POST http://127.0.0.1:8080/web/auth/login

# peticiones al backend con el nombre de dominio para validar la configuración
curl -X POST https://main.chanim.com.gt/web/auth/login
```