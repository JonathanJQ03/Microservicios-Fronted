# <span style="color:#1E90FF;">Sistema de Productos y Categorías con Microservicios</span>

**Autor:** Jonathan Jaguaco  
**Fecha:** 2025-08-13

---

## <span style="color:#32CD32;">Descripción del Proyecto</span>
Este proyecto implementa un sistema modular para gestionar **Productos** y **Categorías** utilizando microservicios.  
Cada componente (frontend, backend, base de datos) corre en contenedores Docker separados y se orquesta mediante Docker Compose.  

Esta arquitectura permite <span style="color:#FF4500;">escalabilidad</span>, <span style="color:#FF4500;">despliegues independientes</span> y un <span style="color:#FF4500;">mantenimiento sencillo</span>.

---

## <span style="color:#32CD32;">Tecnologías Usadas</span>

| Tecnología   | Versión / Detalle                        |
|-------------|-----------------------------------------|
| Java        | 17                                      |
| Spring Boot | Última versión compatible               |
| MySQL       | Imagen oficial Docker más reciente      |
| Angular     | 19                                      |
| Docker      | Docker Engine + Docker Compose          |

---

## <span style="color:#32CD32;">Estructura del Proyecto</span>

```text
.
├── backend/               # Microservicios backend: producto y categoría
├── frontend/              # Aplicación frontend Angular
├── docker-compose.yml     # Orquestación de todos los contenedores
```
<span style="color:#32CD32;">Despliegue en Servidor Ubuntu (Ej. EC2 AWS)</span>

# 1️⃣ Requisitos Previos
# Servidor Ubuntu 22.04 o superior.
# Acceso SSH al servidor.
# Git instalado (si no, se instalará automáticamente).
# Conexión a Internet para descargar imágenes Docker y código fuente.

# 2️⃣ Conexión al Servidor
ssh -i /ruta/a/tu-clave.pem ubuntu@<IP_DEL_SERVIDOR>

# 3️⃣ Preparar el Servidor
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose git
sudo systemctl enable docker --now
sudo usermod -aG docker $USER
# ⚠️ Cierra sesión SSH y vuelve a conectarte para aplicar los permisos.

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
