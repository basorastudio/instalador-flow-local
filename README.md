[![Grupo do WhatsApp](https://img.shields.io/badge/Grupo_Whatsapp-FlowDeskPro-blue)](https://chat.whatsapp.com/Ge1rB20Cp6JA5QbIX4ZulJ) 

## Instalador para uso em Local (Linux)
Probado en Ubuntu 20 y 22

**IMPORTANTE:** Editar archivo `config` y colocar contraseñas de su preferencia e IP de la máquina Ubuntu local

La opción actualizar tomará la última versión del repositorio usado para instalar

---

## 📋 EJECUTAR LOS COMANDOS EN ORDEN

### 1. Actualizar el sistema (OBLIGATORIO)
Para evitar errores, se recomienda actualizar el sistema y reiniciar:

```bash
apt -y update && apt -y upgrade
```

### 2. Reiniciar el sistema
```bash
reboot
```

### 3. Después de reiniciar, continuar con la instalación

**3.1** Navegar al directorio root:
```bash
cd /root
```

**3.2** Clonar el repositorio:
```bash
git clone https://github.com/basorastudio/instalador-flow-local.git instaladorflowlocal
```

**3.3** Editar configuración con sus datos (para guardar: `Ctrl + X`, luego `Y`, luego `Enter`):
```bash
nano ./instaladorflowlocal/config
```

**3.4** Dar permisos de ejecución:
```bash
chmod +x ./instaladorflowlocal/flow
```

**3.5** Cambiar al directorio del instalador:
```bash
cd ./instaladorflowlocal
```

**3.6** Ejecutar el instalador:
```bash
./flow
```

> **Nota:** No es necesario usar `sudo` ya que estamos en el directorio `/root`

---

## ⚙️ Configuración Requerida

Antes de ejecutar el instalador, **DEBE** editar el archivo `config` y modificar:

- `deploy_password`: Contraseña para el usuario deploy
- `mysql_root_password`: Contraseña para MySQL root
- `db_pass`: Contraseña para la base de datos
- `pg_pass`: Contraseña para PostgreSQL
- `redis_pass`: Contraseña para Redis
- `ipservidorubuntu`: IP de su servidor (por defecto: localhost)

---

## ¿Problemas de conexión con whatsapp? ##

Intente actualizar el Conector WWebJS whatsapp.js


## Alterar Frontend

Para cambiar el nombre de la aplicación:

/home/deploy/flowdeskpro/frontend/quasar.conf

/home/deploy/flowdeskpro/frontend/src/index.template.html

Para alterar logos e iconos:

carpeta /home/deploy/flowdeskpro/frontend/public

Para alterar colores:

/home/deploy/flowdeskpro/frontend/src/css/app.sass

/home/deploy/flowdeskpro/frontend/src/css/quasar.variables.sass

Siempre alterar usando usuario deploy, puede conectar al servidor con la aplicación Bitvise SSH Client. Después de las alteraciones compilar nuevamente el Frontend

```bash
su deploy
```
```bash
cd /home/deploy/flowdeskpro/frontend/
```
```bash
npm run build
```

Probar las alteraciones en pestaña anónima

## Errores

"Internal server error: SequelizeConnectionError: could not open file \"global/pg_filenode.map\": Permission denied"

```bash
docker container restart postgresql
```
```bash
docker exec -u root postgresql bash -c "chown -R postgres:postgres /var/lib/postgresql/data"
```
```bash
docker container restart postgresql
```

## Problemas para enviar audios y notificaciones

Esto es porque no posee certificado cuando ejecuta localmente, consideran la conexión como insegura y bloquean el micrófono.

Puede resolver esto accediendo al enlace dentro del navegador Chrome; chrome://flags/#unsafely-treat-insecure-origin-as-secure e insertando la ip con puerto de su frontend y backend.

## Acceso Portainer generar contraseña
"Your Portainer instance timed out for security purposes. To re-enable your Portainer instance, you will need to restart Portainer."

```bash
docker container restart portainer
```

Después acceda nuevamente a la url http://suip:9000/

## Consultoría particular

Para quien le gustaría una consultoría o que yo haga la instalación puede llamar al whatsapp 45 991519978 (será cobrado por eso)

