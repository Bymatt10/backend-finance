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
- 
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
