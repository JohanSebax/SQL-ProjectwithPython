# Descripción del proyecto SQL

El coronavirus tomó al mundo entero por sorpresa, cambiando la rutina diaria de todos y todas. Los habitantes de las ciudades ya no pasaban su tiempo libre fuera, yendo a cafés y centros comerciales; sino que más gente se quedaba en casa, leyendo libros. Eso atrajo la atención de las startups (empresas emergentes) que se apresuraron a desarrollar nuevas aplicaciones para los amantes de los libros.

Te han dado una base de datos de uno de los servicios que compiten en este mercado. Contiene datos sobre libros, editoriales, autores y calificaciones de clientes y reseñas de libros. Esta información se utilizará para generar una propuesta de valor para un nuevo producto.

# Descripción de los datos

**`books`**

Contiene datos sobre libros:

- `book_id`: identificación del libro
- `author_id`: identificación del autor o autora
- `title`: título
- `num_pages`: número de páginas
- `publication_date`: fecha de la publicación
- `publisher_id`: identificación de la editorial

**`authors`**

Contiene datos sobre autores:

- `author_id`: identificación del autor o autora
- `author`: el autor o la autora

**`publishers`**

Contiene datos sobre editoriales:

- `publisher_id`: identificación de la editorial
- `publisher`: la editorial

**`ratings`**

Contiene datos sobre las calificaciones de usuarios:

- `rating_id`: identificación de la calificación
- `book_id`: identificación del libro
- `username`: el nombre del usuario que revisó el libro
- `rating`: calificación

**`reviews`**

Contiene datos sobre las reseñas de los y las clientes:

- `review_id`: identificación de la reseña
- `book_id`: identificación del libro
- `username`: el nombre del usuario que revisó el libro
- `text`: el texto de la reseña

# Ejercicios

- Encuentra el número de libros publicados después del 1 de enero de 2000.
- Encuentra el número de reseñas de usuarios y la calificación promedio para cada libro.
- Identifica la editorial que ha publicado el mayor número de libros con más de 50 páginas (esto te ayudará a excluir folletos y publicaciones similares de tu análisis).
- Identifica al autor que tiene la más alta calificación promedio del libro: mira solo los libros con al menos 50 calificaciones.
- Encuentra el número promedio de reseñas de texto entre los usuarios que calificaron más de 50 libros.

## Conectarse a la base de datos

Usa el siguiente código para crear una conexión a la base de datos:

```bash
# importar librerías
import pandas as pd
from sqlalchemy import create_engine


db_config = {'user': 'practicum_student',         # nombre de usuario
             'pwd': 's65BlTKV3faNIGhmvJVzOqhs', # contraseña
             'host': 'rc1b-wcoijxj3yxfsf3fs.mdb.yandexcloud.net',
             'port': 6432,              # puerto de conexión
             'db': 'data-analyst-final-project-db'}          # nombre de la base de datos

connection_string = 'postgresql://{}:{}@{}:{}/{}'.format(db_config['user'],
                                                        db_config['pwd'],
                                                        db_config['host'],
                                                        db_config['port'],
                                                        db_config['db'])

engine = create_engine(connection_string, connect_args={'sslmode':'require'})

# ejecutar una consulta SQL utilizando pandas

pd.io.sql.read_sql(query, con = engine)
```
## 🛠 Skills

![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)

![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)

**sqlalchemy**

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)

## Lessons Learned

Aprendi a conectarme a una base de datos utilizando Python y algunas librerias como sqlalchemy. Pude ejecutar consultas SQL utilizando Python.

# Conclusiones

- Se pudo notar que 821 libros fueron publicados despues del 1 de Enero del 2020. Es una cantidad de libros considerable.

- El libro con el mayor numero de reseñas es Twilight (Twilight #1) aunque la calificacion promedio no es tan alta. Parece que los libros con mejor calificacion promedio son los de Harry Potter, por ejemplo Harry Potter and the Prisoner of Azkaban.

- La editorial que ha publicado el mayor numero de libros con más de 50 paginas es Penguin Books seguida de Vintage.

- Los autores con la mas alta calificacion promedio para los libros que tiene al menos 50 calificacion son J.K. Rowling/Mary GrandPré, estos autores representan las mejores calificaciones promedio entre los diferentes libros publicados.

- En promedio tenemos aproximadamente 24 reseñas entre los usuarios que calificaron más de 50 libros.
