# Microservicio Shoop
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)

![IntelliJ IDEA](https://img.shields.io/badge/IntelliJIDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

## 🛠 Tecnologías Utilizadas
- Java
- Spring Boot
- MongoDB
- IntelliJ IDEA
- Postman
- 
## Estrutura de los micro servicios de la app
| Microservicio | Metodos | DB |
|----------|----------|----------|
| Productos  | Post | `NOSQL` MongoDB | 

> No es necesario utilizar `IntelliJ IDEA` puedes utilizar cualquier otro IDE que soporte java.

## Microservicio de **Productos**

### Config de dependencia 

| Dependencias | Tipo |
|----------|----------|
| Spring Web | Cell 2   |
| Lombok | WEB |
| Spring Data MongoDB | NOSQL |

conexion con la bd de mongodb
```properties
spring.data.mongodb.uri=mongodb://localhost:27017/ms_productdb
```
### Consultas Postman

POST
```url
localhost:8080/api/v1/products
```
```json
{
    "productName":"laptop",
    "productDescription":"gob lap",
    "unitPrice":2790
}

```
<!--
https://start.spring.io/#!type=maven-project&language=java&platformVersion=3.2.4&packaging=jar&jvmVersion=17&groupId=com.monnsmonsh&artifactId=product-microservice&name=product-microservice&description=Product%20Service&packageName=com.monnsmonsh.product-microservice&dependencies=lombok,web,data-mongodb
-->

### Conexion con eureka service
Para conectar nuestro micro servicion tendremos que agregar una nueva dependendia para ello nos dirigiremos al archivo `pom.xml`.
```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    <version>4.1.1</version>
</dependency>
```
despues configuramos nuestro server en `application.properties`
```properties
spring.application.name=product-microservice
server.port=0
##llaver de configuracion
eureka.instance.instance-id=${spring.application.name}:${random.uuid}
```



## Microservicio de **Reservas**
### Config de dependencias de spring 

| Dependencias | Tipo |
|----------|----------|
| Spring Web | Cell 2   |
| Lombok | WEB |
| Spring Data JPA | SQL |
| MySQL Driver | SQL | 

conexion con la bd de mysql
```properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

spring.datasource.url=jdbc:mysql://localhost:3306/ms_bookingdb
spring.datasource.username=root
spring.datasource.password=*******
spring.jpa.generate-dll=true

```

<!--
https://start.spring.io/#!type=maven-project&language=java&platformVersion=3.2.4&packaging=jar&jvmVersion=17&groupId=com.monnsmonsh&artifactId=booking-microservice&name=booking-microservice&description=Product%20Service&packageName=com.monnsmonsh.booking-microservice&dependencies=lombok,web,data-jpa,mysql
-->

## Servidor Eureka

| Dependencias | Tipo |
|----------|----------|
| Eureka Server | SPRING CLOUD DISCOVERY |

<!--
https://start.spring.io/#!type=maven-project&language=java&platformVersion=3.2.4&packaging=jar&jvmVersion=17&groupId=com.monnsmonsh&artifactId=discovery-service&name=discovery-service&description=Discovery%20Service&packageName=com.monnsmonsh.discovery-service&dependencies=cloud-eureka-server
-->

