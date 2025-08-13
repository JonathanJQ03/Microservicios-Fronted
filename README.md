# <span style="color:#1E90FF;">Sistema de Productos y Categorías con Microservicios</span>

**Autor:** Jonathan Jaguaco  
**Fecha:** 2025-08-13

---

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

# 1. Requisitos Previos
 a. Servidor Ubuntu 22.04 o superior.
 b. Acceso SSH al servidor (Tener instalado el servicio de SSH).
 c. Git instalado (si no, se instalará automáticamente).
 d. Conexión a Internet para descargar imágenes Docker y código fuente.

# 2️⃣ Conexión al Servidor (Usarlo desde la consola de comandos "CMD")
ssh -i "C:\Users\jonat\Desktop\Software\AWS\Docker-Security-Web.pem" ubuntu@ec2-3-138-41-233.us-east-2.compute.amazonaws.com

# 3️⃣ Preparar el Servidor (Una vez ejecutado el comando "ssh" de arriba ya podemos ejecutar los siguientes comandos)
sudo apt update && sudo apt upgrade -y (Este paso puede demorar más, se requiere tambien de salir de la consola ubunto y volver a ingresar con la coenxión del paso 2)
sudo apt install -y docker.io docker-compose git
sudo systemctl enable docker --now
sudo usermod -aG docker $USER
(Una vez ejecutado este ultimo comando volver a salir y entrar para instanciar los clientes docker, realizar el ingreso con el paso 2)

# 4️⃣ Clonar el Repositorio
git clone https://github.com/JonathanJQ03/Microservicios-Fronted.git
cd Microservicios-Fronted

# 5️⃣ Levantar Contenedores con Docker Compose
docker-compose up -d
# Esto descargará todas las imágenes necesarias y levantará los servicios según tu docker-compose.yml

# 6️⃣ Verificar Contenedores
docker ps
# Deberías ver todos los contenedores (MySQL, backend, frontend) en ejecución.

# 7️⃣ Acceder al Frontend
# Abre tu navegador y visita:
http://<IP_DEL_SERVIDOR>:8080

<span style="color:#32CD32;">Notas</span>
text
Copiar
Editar
- El backend se conecta automáticamente a MySQL mediante las variables de entorno definidas en Docker Compose.
- Todos los datos de MySQL se persisten en un volumen Docker definido en docker-compose.yml.
- Cada microservicio puede actualizarse y desplegarse de forma independiente.
