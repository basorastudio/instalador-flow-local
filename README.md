[![Grupo do WhatsApp](https://img.shields.io/badge/Grupo_Whatsapp-FlowDeskPro-blue)](https://chat.whatsapp.com/Ge1rB20Cp6JA5QbIX4ZulJ) 

## Instalador para uso em Local (Linux)
Probado en ubuntu 20 y 22

Editar archivo config y colocar contraseñas de su preferencia e ip de la máquina ubuntu local

La opción actualizar tomará la última versión del repositorio usado para instalar


## EJECUTAR LOS COMANDOS DE ABAJO ##

para evitar errores se recomienda actualizar el sistema y después de actualizar reiniciar para evitar errores

```bash
apt -y update && apt -y upgrade
```
```bash
reboot
```

Después de reiniciar continuar con la instalación

```bash
cd /root
```
```bash
git clone https://github.com/basorastudio/instalador-flow-local.git instaladorflowlocal
```
Editar datos con sus datos, con nano para guardar presiona Ctrl + x
```bash
nano ./instaladorflowlocal/config
```
```bash
sudo chmod +x ./instaladorflowlocal/flow
```
```bash
cd ./instaladorflowlocal
```
```bash
sudo ./flow
```

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

