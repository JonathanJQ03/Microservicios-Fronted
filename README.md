# <span style="color:#1E90FF;">Sistema de Productos y Categorías con Microservicios</span>

**Autor:** Jonathan Jaguaco  
**Fecha:** 2025-08-13

---
###NOTA PODEMOS ACCCEDER DIRECTAMENTE COLOCANDO ESTA DIRECCION: http://3.138.41.233:8080

# <span style="color:#32CD32;">Descripción del Proyecto</span>
Este proyecto implementa un sistema modular para gestionar **Productos** y **Categorías** utilizando microservicios.
Cada componente (frontend, backend, base de datos) corre en contenedores Docker separados y se orquesta mediante Docker Compose.  

---

# <span style="color:#32CD32;">Tecnologías Usadas</span>

| Tecnología   | Versión / Detalle                      |
|-------------|-----------------------------------------|
| Java        | 17                                      |
| Spring Boot | Última versión compatible               |
| MySQL       | Imagen oficial Docker más reciente      |
| Angular     | 19 / 20                                 |
| Docker      | Docker Engine + Docker Compose          |
| Cloud       | AWSEC2 / Servicio en la Nube            |
---

# <span style="color:#32CD32;">Estructura del Proyecto</span>

```text
.
├── backend/               # Microservicios backend (Spring Boot 17 + MySQL)
│   ├── producto/          # Servicio de gestión de productos
│   └── categoria/         # Servicio de gestión de categorías
├── frontend/              # Aplicación frontend Angular 19/20
├── docker-compose.yml     # Orquestación de contenedores Docker (backend, frontend, DB)
├── README.md              # Documentación del proyecto
└── scripts/               # Scripts de despliegue o configuración

```
<span style="color:#32CD32;">Despliegue en Servidor Ubuntu (Ej. EC2 AWS)</span>

# 1. 🛠️ Requisitos Previos

- **Servidor Ubuntu 22.04 o superior**  

- **Acceso SSH al servidor**  
  *(Asegúrate de que el servicio SSH esté instalado y corriendo.)*  

- **Git instalado**  
  *(Si no está instalado, se instalará automáticamente durante el proceso.)*  

- **Conexión a Internet**  
  *(Necesaria para descargar imágenes Docker y el código fuente.)*

# 2️⃣ Conexión al Servidor (Usarlo desde la consola de comandos "CMD")

Para conectarte a tu instancia EC2 mediante SSH, utiliza el siguiente comando:

```bash
ssh -i "C:\Users\jonat\Desktop\Software\AWS\Docker-Security-Web.pem" ubuntu@ec2-3-138-41-233.us-east-2.compute.amazonaws.com
⚠️ Importante:
La ruta de acceso "C:\Users\jonat\Desktop\Software\AWS\Docker-Security-Web.pem" debe existir en tu computadora local, por ende debemos descargar el emp y guardarlo en su maquina.
Copia la ruta completa de tu archivo .pem y pégala en lugar de la ruta que aparece por defecto en el comando.

```

# 3️⃣ Preparar el Servidor
(Una vez ejecutado el comando `ssh` del paso 2, ya podemos ejecutar los siguientes comandos)

```bash
# Actualizar paquetes y sistema
sudo apt update && sudo apt upgrade -y
# ⚠️ Este paso puede demorar varios minutos. 
# Después de la actualización, es recomendable salir de la sesión SSH y volver a conectarse.

# Instalar Docker, Docker Compose y Git
sudo apt install -y docker.io docker-compose git

# Habilitar Docker al iniciar el sistema y arrancarlo ahora
sudo systemctl enable docker --now

# Agregar al usuario actual al grupo docker
sudo usermod -aG docker $USER
# ⚠️ Después de ejecutar este comando, sal de la sesión SSH y vuelve a ingresar 
# siguiendo el paso 2 para que los cambios tengan efecto y puedas ejecutar comandos Docker sin sudo.
```

# 4️⃣ Clonar el Repositorio
(Este paso se realiza dentro de la consola de Ubuntu, una vez conectado vía SSH)

```bash
# Clonar el repositorio desde GitHub
git clone https://github.com/JonathanJQ03/Microservicios-Fronted.git

# Entrar al directorio del proyecto clonado
cd Microservicios-Fronted
Luego:
cd SistemaProductosCategor-as.-main
ls -la (Para verificar que estamos dentro de la carpeta raiz)

```
# 5️⃣ Levantar Contenedores con Docker Compose
(Este paso se realiza dentro del directorio del proyecto clonado en tu instancia Ubuntu)

```bash
# Levantar todos los contenedores en segundo plano
docker-compose up -d
ml
```
# 6️⃣ Verificar Contenedores
(Para asegurarte de que todos los servicios están corriendo correctamente)

```bash
# Listar todos los contenedores en ejecución
docker ps
```

```bash
# 7️⃣ Acceder al Frontend

Abre tu navegador y visita:

http://<IP_DEL_SERVIDOR>:8080](http://3.138.41.233:8080

⚠️ **Notas importantes:**  
- El backend se conecta automáticamente a MySQL mediante las variables de entorno definidas en `docker-compose.yml`.  
- Todos los datos de MySQL se persisten en un **volumen Docker** definido en `docker-compose.yml`.  
- Cada microservicio puede actualizarse y desplegarse de forma independiente.
```
