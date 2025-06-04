# CERTIFICADOS

```bash
# Crear el archivo .pem a través del .cert y .ca desde GITBASH
cat mia.chanim.com.gt.cert mia.chanim.com.gt.ca > mia.chanim.com.gt.pem

# Subirlo al static publico para descargarlo y luego eliminarlo
wget https://static.utzsystem.com/mia.chanim.com.gt.pem -O mia.chanim.com.gt.pem
wget https://static.utzsystem.com/mia.chanim.com.gt.key -O mia.chanim.com.gt.key
```