# Práctica SEO

Maquetación SEO de una página web de currículum.

Enlace a la web: https://ferveloper.github.io/mod-seo-web-cv/

## Esquema general del documento

De acuerdo a las buenas prácticas del SEO, se ha estructurado el documento web con los siguientes criterios.

La estructura de la web se compone de un único encabezado `h1` situado dentro del `header`. Las diferentes secciones del CV están envueltas en etiquetas `section` y encabezadas por un `h2`. Las subsecciones, donde son necesarias, están encabezadas por un `h3`. La estructura de encabezados queda de la siguiente manera:

- **h1:** Fernando Merino
  - **h2:** Quién soy
  - **h2:** Estudios
    - **h3:** VI Full Stack Web Bootcamp
    - **h3:** Full Stack Development Program
    - **h3:** Ingeniero Industrial
    - **h3:** Ingeniero Técnico Industrial
  - **h2:** Experiencia
    - **h3:** PV Project Engineer
    - **h3:** Project Engineer
    - **h3:** Ingeniero de I+D
  - **h2:** Sobre mí
  - **h2:** Contacto

Existe menú lateral único y responsive dentro del header que contiene los enlaces a las diferentes secciones del documento, marcadas con etiquetas `section` y su `id` identificativa para la navegación.

Los contenidos de `section` tienen un ancho del 75% para dejar espacio al menú lateral, y por maquetación, están contenidas dentro de etiquetas `div` con el ancho de pantalla para aplicar los colores de fondo.

Finalmente, en el `footer` se ubican los enlaces a los perfiles sociales.

## Acciones realizadas de cara al SEO

Siguiendo las recomendaciones del SEO, se han realizado las siguientes acciones de optimización:

- Etiqueta `title` optimizado para búsquedas por el nombre y profesión del autor. Longitud de 60 caracteres, por debajo del máximo mostrado en las SERP de Google, buscador de referencia.
- Añadida etiqueta meta description de 144 caracteres, por debajo del máximo mostrado en las SERP de Google, buscador de referencia.
- Una única hoja de estilos cargada en el `header` para optimizar la carga.
- El script de JS es llamado al final del body para evitar cualquier posibler bloqueo de la carga de HTML.
- Incluidas en las etiquetas `a` el atributo `title` en con información concreta sobre el enlace para facilitar el rastreo a las arañas de los buscadores.
- Uso de etiquetas `abbr` para definir las abreviaturas que aparecen en los textos.
- Foto maquetada mediante las etiquetas `figure` y `figcaption`.
- Todos los textos que aparecen en la web en mayúsculas están escrito en el HTML en formato de frase normal y se ponen en mayúsculas mediante CSS (`text-transform: uppercase`).
- Uso de la etiqueta `address` en el footer para marcar los perfiles sociales de contacto.

## Microdatos

Para el marcado de los microdatos en formato schema.org, se ha empleado como base el objeto de tipo `Person` (<https://schema.org/Person>). Las propiedades empleadas han sido las siguientes:

- `name`: Nombre completo
- `givenName`: Nombre
- `familyName`: Apellido
- `image`: Imagen de la persona
- `description`: Descripción de la persona
- `hasOccupation`: Profesión. Objeto de tipo `Role` (<https://schema.org/Role>), con las propiedades:
  - `name`: Nombre de la profesión
  - `startDate`: Nombre de la profesión
- `birthPlace`: Lugar de nacimiento. Objeto de tipo `Place` (<https://schema.org/Role>), con la propiedad:
  - `name`: Nombre del lugar
- `alumniOf`: Instituciones en las que ha estudiado. Detallado más adelante
- `worksFor`: Empresa para la que trabaja actualmente. Detallado más adelante
- `memberOf`: Empresas para las que ha trabajado. Detallado más adelante
- `contactPoint`: Punto de contacto. Detallado más adelante

 Para disponer de todas las propiedades necesarias para marcar el CV dentro de un JSON único, se han empleado tipos adicionales en secciones específicas, las cuáles se detallan a continuación.

### Sección _"Estudios"_

Para conectar a la persona con sus estudios, se parte de la propiedad `alumniOf` y se anidan de forma combinada los tipos `EducationalOrganization` y `OrganizationRole`. Para las universidades se emplea `CollegeOrUniversity` en lugar de `EducationalOrganization`. Esto permite disponer de las siguientes propiedades de ambos tipos:

- `name`: Nombre de la organización educativa
- `description`: Descripción de los estudios
- `startDate`: Fecha de inicio
- `endDate`: Fecha de finalización

### Sección _"Experiencia"_

Para conectar a la persona con su experiencia laboral, se parte de las propiedades `worksFor` (para su empleo actual) y `memberOf` (para empleos pasados) y se anidan de forma combinada los tipos `Organization` y `OrganizationRole`. Esto permite disponer de las siguientes propiedades de ambos tipos:

- `name`: Nombre de la empresa
- `rolName`: Nombre del puesto de trabajo
- `description`: Descripción del puesto de trabajo
- `startDate`: Fecha de inicio
- `endDate`: Fecha de finalización

### Sección _"Contacto"_

Para indicar los puntos de contacto de la persona se emplea la propiedad `contactPoint` y el tipo `ContactPoint`. Esto permite disponer de las siguientes propiedades:

- `name`: Nombre del punto de contacto
- `url`: URL del punto de contacto
