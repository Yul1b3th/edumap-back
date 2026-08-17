# API de Distritos de Barcelona

API REST para consultar información sobre los distritos de Barcelona,
incluyendo datos de renta y oferta educativa.

El proyecto está construido con Spring Boot, Spring WebFlux y R2DBC,
utilizando MySQL como base de datos.

---

## Tecnologías

- Java 21
- Spring Boot 3
- Spring WebFlux
- Spring Data R2DBC
- MySQL
- Gradle
- Swagger / OpenAPI

---

## Requisitos

Para ejecutar el proyecto localmente necesitas:

- Java 21
- Git
- MySQL
- Un cliente para administrar MySQL (opcional)

---

## Instalación

### 1. Clonar el repositorio

```bash
git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_PROYECTO>
```

### 2. Crear la base de datos

Crear una base de datos MySQL local:

```sql
CREATE DATABASE edumap;
```

### 3. Importar los datos

El proyecto necesita la estructura y los datos de la base de datos.

Importar los archivos SQL del proyecto:

- `schema.sql` → crea las tablas
- `data.sql` → inserta los datos


---

## 4. Configurar la conexión a MySQL

Configurar las siguientes variables de entorno:

```text
DATABASE_URL=r2dbc:mysql://localhost:3306/edumap
DATABASE_USERNAME=tu_usuario
DATABASE_PASSWORD=tu_password
```

El proyecto utiliza estas variables en:

`src/main/resources/application.properties`

```properties
spring.r2dbc.url=${DATABASE_URL}
spring.r2dbc.username=${DATABASE_USERNAME}
spring.r2dbc.password=${DATABASE_PASSWORD}
```

---

## 5. Ejecutar el proyecto

Desde la raíz del proyecto:

### Windows

```bash
.\gradlew.bat bootRun
```

### Linux / macOS

```bash
./gradlew bootRun
```

Por defecto, la aplicación utiliza el puerto `8080`.

La API estará disponible en:

```text
http://localhost:8080
```

---

## Endpoints

1. **GET `/api/districts/`**
    - **Descripción**: Obtiene una lista de todos los distritos con sus datos de renta.
    - **Respuesta**:
        - **200**: Lista de distritos con sus datos de renta.
        - **404**: No se encontraron distritos.
        - **500**: Error interno del servidor.
```json
[
  {
    "id": 0,
    "name": "string",
    "valor": 0,
    "colorIndex": 0
  }
]
```
2. **GET `/api/districts/infantil`**
   - **Descripción**: Obtiene la lista de distritos con el número total de centros educativos de Infantil y su porcentaje correspondiente.
   - **Respuesta**:
      - **200**: Lista de distritos con el total de centros de Infantil y el porcentaje.
      - **404**: No se encontraron datos para la educación infantil.
      - **500**: Error interno del servidor.
    ```json
    [
      {
        "id": 1,
        "name": "Ciutat Vella",
        "total": 18,
        "percentage": 5.248618784530387
      }
    ]
    ```

3. **GET `/api/districts/primary`**
   - **Descripción**: Obtiene la lista de distritos con el número total de centros educativos de Primaria y su porcentaje correspondiente.
   - **Respuesta**:
      - **200**: Lista de distritos con el total de centros de Primaria y el porcentaje.
      - **404**: No se encontraron datos para la educación primaria.
      - **500**: Error interno del servidor.
    ```json
    [
      {
        "id": 1,
        "name": "Ciutat Vella",
        "total": 18,
        "percentage": 5.389221556886228
      }
    ]
    ```

4. **GET `/api/districts/secondary`**
   - **Descripción**: Obtiene la lista de distritos con el número total de centros educativos de Secundaria y su porcentaje correspondiente.
   - **Respuesta**:
      - **200**: Lista de distritos con el total de centros de Secundaria y el porcentaje.
      - **404**: No se encontraron datos para la educación secundaria.
      - **500**: Error interno del servidor.
    ```json
    [
      {
        "id": 1,
        "name": "Ciutat Vella",
        "total": 14,
        "percentage": 5.957446808510639
      }
    ]
    ```

---

## Documentación de la API

Una vez que la aplicación se esté ejecutando, puede acceder a la documentación de Swagger en:

[https://edumap-back.onrender.com/webjars/swagger-ui/index.html](https://edumap-back.onrender.com/webjars/swagger-ui/index.html)
