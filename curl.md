# Curl

```bash
# peticiones al backend con localhost para validar la configuración
curl -X POST http://127.0.0.1:8080/web/auth/login

# peticiones al backend con el nombre de dominio para validar la configuración
curl -X POST https://main.chanim.com.gt/web/auth/login
```

## WhatsApp
```bash
# Cambiar el verify_token y hacer la prueba antes del dominio y el certificado
curl -i https://mia.chanim.com.gt:3005/
curl -i "https://mia.chanim.com.gt:3005/webhook?hub.mode=subscribe&hub.verify_token=SHERLOCKHOLMES&hub.challenge=123456"

# web
https://mia.chanim.com.gt:3005/
```