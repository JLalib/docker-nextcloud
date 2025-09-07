# Nextcloud con Docker Compose

Este proyecto despliega una instancia de **Nextcloud** con base de datos **MariaDB** usando `docker-compose`.  
Está pensado para ser sencillo de instalar y personalizar tanto en servidores x64 como en Raspberry Pi.

---

## 🚀 Requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Un servidor o máquina con al menos:
  - 2 GB de RAM (recomendado)
  - Espacio en disco suficiente para tus archivos

---

## 📂 Estructura de directorios

Al ejecutar los contenedores, se crearán carpetas locales para persistencia de datos:

```
.
├── compose.yml
├── db/                 # Datos de la base de datos
└── nextcloud/
    ├── config/         # Configuración de Nextcloud
    ├── data/           # Archivos subidos por los usuarios
    ├── custom_apps/    # Aplicaciones adicionales
    └── themes/         # Temas personalizados
```

---

## ⚙️ Configuración

### Variables de entorno importantes

En el archivo `compose.yml` debes cambiar las contraseñas de ejemplo:

```yaml
MYSQL_ROOT_PASSWORD=yourpassword
MYSQL_PASSWORD=yourpassword
```

⚠️ **Importante**: Usa contraseñas seguras y únicas.

### Raspberry Pi / ARM 32 bits

Si instalas en una Raspberry Pi de 32 bits, cambia la imagen de la base de datos en `compose.yml`:

```yaml
image: yobasystems/alpine-mariadb:latest
```

---

## ▶️ Puesta en marcha

1. Clona este repositorio o copia los archivos.
2. Lanza los contenedores:

```bash
docker compose up -d
```

3. Accede a Nextcloud en tu navegador:

- **http://localhost:8080**
- **https://localhost:8443** (si configuras SSL en el contenedor)

4. Completa la instalación inicial en el asistente de Nextcloud.

---

## 🔧 Gestión de contenedores

- **Detener**  
  ```bash
  docker compose down
  ```
- **Reiniciar**  
  ```bash
  docker compose restart
  ```
- **Ver logs**  
  ```bash
  docker compose logs -f
  ```

---

## 🌐 SSL y Reverse Proxy

Para entornos en producción se recomienda configurar un **reverse proxy** como [NGINX Proxy Manager](https://nginxproxymanager.com/) o [Traefik](https://traefik.io/) para manejar certificados SSL con Let's Encrypt.

---

## 📖 Recursos adicionales

- [Documentación oficial de Nextcloud](https://docs.nextcloud.com/)
- [Nextcloud Docker Hub](https://hub.docker.com/_/nextcloud)
- [MariaDB Docker Hub](https://hub.docker.com/_/mariadb)

