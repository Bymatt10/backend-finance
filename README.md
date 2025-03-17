# backend-finance
# 💰 Personal Finance App Backend

Backend para la aplicación de finanzas personales.  
Construido con **Spring Boot**, autenticación con **Auth0**, base de datos **MySQL**, caché con **Redis**, y orquestado con **Docker Compose**.

---

## 🛠️ Tecnologías usadas

- **Spring Boot 3+**
- **Spring Security + Auth0 (OAuth2 + JWT)**
- **MySQL 8**
- **Redis 7**
- **Docker Compose**
- **JPA / Hibernate**
- **Lombok**

---

## 🚀 ¿Qué hace este backend?

- Importa archivos de transacciones bancarias y las categoriza automáticamente.
- Soporta múltiples carteras: efectivo, tarjeta de crédito, débito, ahorro.
- Maneja multimoneda (USD, COR, etc.).
- Asocia cada cuenta a un banco específico.
- Usa Redis para caché y mejorar performance.
- Seguridad mediante Auth0 con JWT.

---

## 📂 Estructura del Proyecto

/backend ┣ /src ┃ ┣ /main ┃ ┃ ┣ /java/com/yourapp ┃ ┃ ┃ ┣ config --> Configuración de seguridad (Auth0), CORS, Redis ┃ ┃ ┃ ┣ controller --> Endpoints REST ┃ ┃ ┃ ┣ model --> Entidades: User, Wallet, Transaction, Category ┃ ┃ ┃ ┣ repository --> Repositorios JPA ┃ ┃ ┃ ┣ service --> Lógica de negocio ┃ ┃ ┃ ┗ Application.java --> Clase principal ┃ ┃ ┗ /resources ┃ ┃ ┃ ┣ application.yml --> Configuraciones de MySQL, Redis, Auth0 ┣ Dockerfile ┗ docker-compose.yml


---

## ⚙️ Configuración inicial

### 1️⃣ Variables importantes en `application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:mysql://mysql-db:3306/finance_app
    username: finance_user
    password: finance_pass
  redis:
    host: redis-cache
    port: 6379
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://YOUR_AUTH0_DOMAIN/
2️⃣ Variables necesarias en Auth0:
Dominio de Auth0
API Audience configurado
Crear aplicación Machine-to-Machine o SPA y obtener los tokens
🐳 Docker Compose

Levantar la base de datos y Redis:

docker-compose up -d
Esto levanta:

Servicio	Puerto	Usuario/Contraseña
MySQL	3306	finance_user / finance_pass
Redis	6379	No requiere autenticación por defecto
🔑 Configuración Auth0

Crear un tenant en Auth0
Configurar:
API → Audience: finance-api
Application → Machine-to-Machine o SPA
En Spring Boot, configurar issuer-uri y Audience en el .yml.
📝 Endpoints principales

Método	Endpoint	Descripción
GET	/api/wallets	Listar carteras del usuario autenticado
POST	/api/wallets	Crear nueva cartera
POST	/api/transactions/import	Importar archivo de transacciones (parsing)
GET	/api/transactions	Listar transacciones
GET	/api/categories	Listar categorías
🚀 Cómo correr localmente

# Levantar MySQL y Redis
docker-compose up -d

# Correr la app Spring Boot
./mvnw spring-boot:run
