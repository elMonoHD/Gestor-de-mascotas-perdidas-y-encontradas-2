# Gestor-de-mascotas-perdidas-y-encontradas-2

Descripción breve del sistema
Este sistema es una plataforma web para la gestión de mascotas perdidas y encontradas.

Permite a los usuarios:


Registrar mascotas perdidas o encontradas mediante publicaciones.


Comentar en publicaciones para ayudar a reunir mascotas con sus dueños.


Adoptar mascotas disponibles.


Los administradores (empleados) pueden moderar publicaciones, gestionar mascotas y usuarios.


Hay dos tipos de usuarios:


Clientes: pueden registrarse, crear publicaciones, comentar y adoptar mascotas.


Empleados (Admins): tienen acceso completo al sistema, gestionar publicaciones y mascotas.


Diagrama de modelos en palabras

El sistema está compuesto por los siguientes modelos y relaciones:


1. User (Usuario)
Es el modelo base proporcionado por Django (django.contrib.auth.models.User).


Representa a todos los usuarios registrados del sistema (clientes y empleados).


2. UserProfile

Tiene una relación uno a uno con el modelo User.


Contiene un campo user_type que indica si el usuario es un Cliente o un Empleado.



Relación:

User 1 ── 1 UserProfile

UserProfile.user_type es una FK a UserType


3. UserType

Modelo que define los tipos de usuario: "Cliente" o "Empleado".

Es utilizado por UserProfile.

4. Mascota

Representa una mascota en el sistema.

Contiene campos como nombre, raza y foto.

5. Estado

Define si una publicación es sobre una mascota perdida o encontrada.


Tiene un solo campo nombre.


6. Publicacion

Es el modelo principal del sistema.

Representa un caso publicado por un usuario sobre una mascota.

Contiene:

La mascota asociada (FK a Mascota)

El usuario que publicó (FK a User)

El estado (FK a Estado)

Información como lugar, contacto, descripción y fecha.

Relaciones:

Publicacion ──> Mascota

Publicacion ──> Usuario

Publicacion ──> Estado

7. Comentario

Comentarios que los usuarios dejan en publicaciones.

Cada comentario pertenece a una Publicacion y tiene un autor (User).

Tiene texto y fecha.

Relaciones:

Comentario ──> Publicacion

Comentario ──> Usuario

8. Adopcion

Representa que un usuario adoptó una mascota.

Guarda la mascota adoptada, el usuario que la adoptó y la fecha.

Relaciones:


Adopcion ──> Mascota

Adopcion ──> Usuario


Intrucciones para ejecutar el backend y el front

Backend:

En la consola del visual situarse en la carpeta del proyecto mediante con un “cd gestor_mascotas_backend”
Activar el entorno virtual mediante el comando “pipenv shell”
Correr el servidor con el comando “python manage.py runserver”
En la url escribir /api

Frontend:
Situarse en la carpeta del proyecto mediante un “cd gestor_mascotas_frontend”
Correr el servidor mediante con el comando “npm start”


