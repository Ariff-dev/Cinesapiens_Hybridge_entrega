
# Sapiens Platform

## Descripción
Sapiens Platform es una aplicación web diseñada para permitir a los usuarios interactuar y gestionar contenido exclusivo. Los usuarios pueden registrarse, iniciar sesión, y dependiendo de su rol (`sapiens` o `admin`), pueden acceder a diferentes funcionalidades, como la creación y gestión de publicaciones en un dashboard exclusivo.

### Tecnologías utilizadas
- **Frontend**: React con React Router y Tailwind CSS para el diseño y enrutamiento de la interfaz de usuario.
- **Backend**: Flask con SQLAlchemy para la gestión de la base de datos, Flask-JWT para la autenticación y autorización con JWT, y Cloudinary para el almacenamiento de imágenes.
- **Base de datos**: PostgreSQL, gestionada mediante DBeaver y Flask-Migrate para el control de versiones de la base de datos.
- **Servidor y despliegue**: Docker y Ubuntu para el entorno del servidor y la configuración de despliegue.

---

## Instalación y configuración

### Requisitos previos
- Python 3.12.3
- Node.js y npm
- Docker (opcional para despliegue en servidor)

### Clonar los repositorios
```bash

backend: 
git clone https://github.com/Ariff-dev/Cinesapiens_Hybridge_backend
cd Cinesapiens_Hybridge_backend

frontend:
git clone https://github.com/Ariff-dev/Cinesapiens_Hybridge_frontend

cd Cinesapiens_Hybridge_frontend

```

### Backend (Flask)

1. **Instalar dependencias**:
    ```bash
    pip install -r requirements.txt
    or
    pip3 install -r requirements.txt
    ```

2. *docker-compose.yml* 
   - **Para postgresql** 

3. **Inicializar la base de datos**:
    ```bash
    flask db init
    flask db migrate
    flask db upgrade
    ```

4. **CORS**: Asegurarse de tener configurado `Flask-CORS` para permitir las peticiones desde el frontend.

5. **Ejecutar el servidor**:
    ```bash
    flask run
    ```

### Frontend (React)

1. **Instalar dependencias**:
    ```bash
    npm install
    ```

2. **Iniciar la aplicación**:
    ```bash
    npm run dev
    ```

### Docker (Opcional para despliegue)

1. **Construir y ejecutar contenedores**:
    ```bash
    docker-compose up --build
    ```

---

## Funcionalidades principales

### Autenticación y Autorización
- **Inicio de sesión y registro** de usuarios con JWT.
- Roles de usuario (`sapiens` y `admin`), gestionados en la base de datos y verificados en el backend para restringir el acceso a ciertas rutas.

### Publicaciones (Posts)
- **Crear, editar y eliminar** publicaciones, limitado a usuarios con rol `sapiens`.
- Los usuarios pueden ver las publicaciones sin autenticación a través de un endpoint público.

### Admin Dashboard
- **Admin Dashboard** para la gestión de los posts, donde los administradores pueden ver todos los posts y los usuarios `sapiens` aplicados o activos.
- **Edición y eliminación de posts** directamente desde el dashboard, con redirección opcional a una página específica de edición.

## API Endpoints

### Auth
- `POST /login`: Autenticación del usuario.
- `POST /signup`: Registro de un nuevo usuario.

### Posts
- `GET /posts`: Obtener todas las publicaciones.
- `POST /create-post`: Crear una publicación (solo `sapiens`).
- `PUT /edit-post/<int:post_id>`: Editar una publicación específica.
- `DELETE /delete-post/<int:post_id>`: Eliminar una publicación específica.

---


## Licencia

Este proyecto está bajo la Licencia MIT.

