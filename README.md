Prueba Técnica Junior: Sistema de Gestión de Curso
Descripción General
Debes desarrollar una aplicación full-stack para gestionar un curso y sus estudiantes. La aplicación permitirá crear, actualizar y eliminar un curso, así como añadir y remover estudiantes. La prueba evalúa tus habilidades en NestJS para el backend y React para el frontend, con énfasis en integración, manejo de errores y una funcionalidad personalizada.
Duración estimada: 30 horas.Entrega: Repositorio de GitHub con el código fuente, instrucciones de instalación y un README con decisiones técnicas y cómo ejecutar la aplicación.

Requisitos del Backend (NestJS)
Tecnologías Obligatorias

Framework: NestJS con TypeScript.
Base de datos: PostgreSQL (usa TypeORM o Prisma).
Validación: Usa class-validator para DTOs.
Estructura: Modular (controladores, servicios, entidades).

Funcionalidades

Gestión del Curso:

POST /course: Crea un curso (nombre, descripción, cupo máximo de estudiantes).
GET /course: Devuelve el curso (solo puede haber un curso en el sistema).
PATCH /course: Actualiza el curso.
DELETE /course: Elimina el curso y sus estudiantes asociados.


Gestión de Estudiantes:

POST /course/students: Añade un estudiante al curso (nombre, email). Valida que no supere el cupo máximo.
GET /course/students: Lista los estudiantes del curso.
DELETE /course/students/:id: Elimina un estudiante del curso.


Requisito Especial:

Calcula un índice de diversidad basado en los dominios de los emails de los estudiantes (ejemplo: @gmail.com, @outlook.com). El índice es el número de dominios únicos dividido por el total de estudiantes, expresado como porcentaje. Devuélvelo en GET /course.
Ejemplo: 5 estudiantes con dominios @gmail.com, @gmail.com, @outlook.com, @yahoo.com, @hotmail.com → (4 dominios únicos / 5 estudiantes) * 100 = 80%.


Manejo de Errores:

Usa códigos HTTP apropiados (200, 201, 400, 404).
Implementa un interceptor para formatear errores (ejemplo: { message: "Error description", statusCode: 400 }).


Optimización:

Añade un índice en la tabla de estudiantes para acelerar la búsqueda por curso.
Cachea el índice de diversidad en memoria (usa un servicio en NestJS) para evitar recalcularlo en cada llamada a GET /course.




Requisitos del Frontend (React)
Tecnologías Obligatorias

Framework: React con TypeScript.
Gestión de Estado: React Query para peticiones HTTP.
Estilos: Tailwind CSS (vía CDN).
Rutas: React Router.
HTTP: Axios.

Funcionalidades

Gestión del Curso:

Página principal (/course) que muestre el nombre, descripción, cupo máximo y el índice de diversidad del curso.
Botón para crear o actualizar el curso (modal con formulario).
Botón para eliminar el curso.


Gestión de Estudiantes:

Sección en la página del curso para listar estudiantes (nombre, email).
Formulario para añadir un estudiante.
Botón para eliminar un estudiante.


Requisito Especial:

Muestra el índice de diversidad con un gauge (medidor) personalizado (sin librerías externas). Usa CSS para crear un semicírculo que se llene según el porcentaje:
< 50%: Rojo.
50-75%: Amarillo.

75%: Verde.




Al pasar el cursor, muestra un tooltip con el cálculo detallado (dominios únicos, total de estudiantes).


Optimización:

Usa useMemo para evitar renders innecesarios en la lista de estudiantes.
Muestra un spinner durante las peticiones HTTP.
Maneja errores con mensajes al usuario (ejemplo: "Cupo máximo alcanzado").




Criterios de Evaluación

Funcionalidad: Cumple todos los requisitos.
Código limpio: Modular, con nombres claros y comentarios necesarios.
Manejo de errores: Respuestas consistentes ante fallos.
Rendimiento: Índices en la base de datos, caché, y optimización en React.
Creatividad: Solución original para el índice de diversidad y el gauge.
Documentación: README con instrucciones y decisiones técnicas.


Restricciones

No uses librerías externas para el gauge del índice de diversidad.
No copies código de tutoriales o plantillas.
Usa datos reales en la base de datos (no mocks estáticos).
Sube el código a un repositorio público en GitHub.


Instrucciones de Entrega

Crea un repositorio en GitHub con carpetas backend (NestJS) y frontend (React).
Incluye un README.md con:
Instrucciones para instalar y ejecutar.
Explicación de decisiones técnicas (ejemplo: por qué usaste Prisma, cómo cacheaste el índice).
Captura o video corto de la aplicación funcionando.


Proporciona un archivo .env.example para variables de entorno.
Comparte el enlace del repositorio.

