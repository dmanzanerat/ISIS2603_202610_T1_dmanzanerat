# Taller Persistencia

## Enlaces de interés

* [BookstoreBack](https://github.com/Uniandes-isis2603/bookstore-back) -> Repositorio de referencia para el Back


# Justificación relaciones

- La relación de la entidad Genre es de many to many, ya que una pelicula puede tener mas de un genero y un genero puede describir mas de una pelicula.
- La relación de la entidad Script es one to one, porque una pelicula solo puede tener un guion y un guion solo puede tener una pelicula.


#Test de integridad

Al intentar eliminar un Director que tiene películas asociadas sin usar cascada, se arroja el error:

```

org.hibernate.exception.ConstraintViolationException: could not execute statement

SQL Error \[23503]: Referential integrity constraint violation

```

El error viene de la relación @ManyToOne en MovieEntity. Crea una foreign key al ser creada, cuando se elimina el director las peliculas quedan con una referencia a una llave inexistence, lo cual no esta permitido.
