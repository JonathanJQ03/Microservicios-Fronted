# 🧩 Proyecto de Microservicios con Spring Boot + MySQL + Docker

Este repositorio contiene una arquitectura de microservicios construida con **Spring Boot**, **MySQL** y orquestada con **Docker Compose**. Permite levantar fácilmente una base de datos y dos microservicios listos para ser ejecutados desde cualquier máquina con Docker instalado.

---

## 📦 Servicios incluidos

- 🟢 mysql → Contenedor de base de datos MySQL (puerto 3306)  
- 🔵 prueba → Microservicio Spring Boot 1 (puerto 8081)  
- 🟣 categoria → Microservicio Spring Boot 2 (puerto 8084)  
- 🟡 producto → Microservicio Spring Boot 3 (puerto 8082)  
- 🌐 catalogo-frontend → Aplicación Angular que consume los microservicios (puerto 8080)  

---

## 🔧 Requisitos previos

- Docker y Docker Compose instalados.
- Puertos `3306`, `8081`, `8084` disponibles (o modificarlos en `docker-compose.yml`).
- Conexión a internet (solo si usas imágenes desde Docker Hub).

---

## 🚀 Instrucciones para ejecutar el proyecto localmente

```bash
# Clona este repositorio
git clone https://github.com/Alexandernacato/EjercicioSpringBoot.git
cd EjercicioSpringBoot

# Construye y levanta todos los contenedores
docker compose up --build

# Espera unos segundos hasta que todo esté listo
# Luego accede a:
# http://localhost:8084   → Microservicio 'categoria'
# http://localhost:8082   → Microservicio 'producto'
# http://localhost:8080   → Aplicación Angular (frontend) "# SistemaProductosCategor-as." 
