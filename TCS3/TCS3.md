

## Título
                           Practica volume

## Tiempo de duración
Esta practica tuvo una duracion de unos 50 minutos.

## Fundamentos



## Conocimientos previos


##  Objetivos a alcanzar
- Implementar dos contenedores uno sin volumen y otro con para verificar la persistencia de los datos


---

## Equipo necesario
- laptop con conexion a Internet
- Docker Desktop instalado localmente 


---

## Material de apoyo
- Documentación oficial de Docker 


---

## Procedimiento
Esta practica la estoy desarrollando en docker instalado localmente en mi maquina

# Parte 1

**Paso 1:** Creación de un contenedor de postgresql sin volumenes 
        
        **COMANDO UTILIZADO**

          docker run -d --name dbpsql_1 -e POSTGRES_PASSWORD=admin -p 5432:5432 postgres

![Figura 1.  Creacion del contenedor de postgresql](Figura1.png)
                                                                                             

**Paso 2:** Acceder al contenedor para crear una base de datos::

    **COMANDO UTILIZADO**

           docker exec -it dbpsql_1 psql -U postgres

![Figura 2.  Accediendo al contenedor de postgresql](Figura2.png)
                                                                                             

**Paso 3:** Crear una base de datos       

     ***COMANDO UTILIZADO***

            CREATE DATABASE Aucay1;

![Figura 3 . Creando base de datos](Figura3.png)


                                                                                             
**Paso 3.1:** Verificar la base de datos      

     ***COMANDO UTILIZADO***

            \l


![Image3.1 Verificacion de las base de datos](image3.1.png)

                                                                                             
**Paso 4:** Salir de la consola de Postgresql y regresar a la terminal de Docker:

     ***COMANDOS UTILIZADOS***
           
            \q

![Figura 4.  Salir de la consola de PostgreSql](Figura4.png)
                                                                                                         


**Paso 5:** Detener el contenedor:

     ***COMANDOS UTILIZADOS***

            docker stop dbpsql_1

![Figura 5 Detener el contenedor](Figura5.png)

                                                                                             
**Paso 6:** volver a iniciar el contenedor:

     ***COMANDOS UTILIZADOS***

            docker start dbpsql_1

![Figura 6.  Volver a iniciar el contenedor](Figura6.png)


                                                                                             
**Paso 7:** Verificar que la base de datos no persiste:

     ***COMANDOS UTILIZADOS***

           docker exec -it dbpsql_1 psql -U postgres
       
              \l


![Figura 7 Verificacion si sigue existiendo la base de datos 'Aucay1'](Figura7.png)
##### La base de datos "Aucay1" ya no debria de existir 

                                                                                             

# Parte 2 
## Crear un contenedor PostgreSQL con volúmenes:

**Paso 8:** Crear un Volumen:

     ***COMANDOS UTILIZADOS***

            docker volume create db_aucay


![Figura 8.  Creacion de un volumen](Figura8.png)

                                                                                             
**Paso 9:** Ejecutar el contenedor PostgreSQL con persistencia:

     ***COMANDOS UTILIZADOS***

            docker run -d --name dbpsql_vol -e POSTGRES_PASSWORD=admin -v db_vol:/var/lib/postgresql/data -p 5433:5432 postgres


![Figura 9. Ejecucion del contenedor con volumen](Figura9.png)

                                                                                             


**Paso 10:**Acceder al contenedor para crear la base de datos:
 
     ***COMANDOS UTILIZADOS***

            docker exec -it dbpsql_vol psql -U postgres


![Figura 10. Acceder al contenedor](Figura10.png)
                                                                                                         
**Paso 11:** Crear la base de datos:

            ***COMANDOS UTILIZADOS***

            CREATE DATABASE Vol_Aucay2;

![Figura 11. Creacion de la base de datos](Figura11.png)
                                                                                              
**Paso 11.1:** Verificar la base de datos      

     ***COMANDO UTILIZADO***

            \l


![Image 11.1 Visualizacion de la base de datos creada](image11.1.png)


**Paso 12:** Salir de la consola de Postgresql y regresar a la terminal de Docker:

     ***COMANDOS UTILIZADOS***
           
            \q

![Figura 12.  Salir de la consola de PostgreSql](Figura12.png)
                                                                                                         


**Paso 13:** Detener el contenedor:

     ***COMANDOS UTILIZADOS***

            docker stop dbpsql_vol

![ Figura 13.  Se detiene el contenedor](Figura13.png)
                                                                                             
**Paso 14:** volver a iniciar el contenedor:

     ***COMANDOS UTILIZADOS***

            docker start dbpsql_vol

![Figura 14. Se vuelve a iniciar el contenedor](Figura14.png)

                                                                                             
**Paso 15:** Verificar que la base de datos persiste:

     ***COMANDOS UTILIZADOS***

           docker exec -it dbpsql_vol psql -U postgres
       
              \l
![Figura 15. Se verifica que la base de datos aun esta existiendo](Figura15.png)

##### La base de datos "Vol_Aucay2" debria de existir todavia



## Resultados esperados 

- Contenedor PostgreSQL sin volúmenes:
Se creó la base de datos Aucay1, pero no persiste después de reiniciar el contenedor.

- Contenedor PostgreSQL con volúmenes:
Se creó la base de datos Vol_Aucay2, la cual sí persiste después de reiniciar el contenedor.



## Bibliografia 
   Docker Inc. (2024). Docker Documentation. Recuperado de https://docs.docker.com/

   Apellido, N. (2024). Guía de administración de servidores Nginx.

   Play with Docker. (2024). Play with Docker Documentation. Retrieved from https://labs.play-with-docker.com




![alt text](image.png)




