# Odoo Instalacion

En este proyecto vamos a montar un servidor de Odoo con una base de datos Postgresql en Docker

Para empezar tenemos que crear un archivo [docker-compose.yml](https://github.com/GorillaGrip/odoo/commit/8d6f09ff7e187558d47d27662984c514928c0552)
Ejemplo:
```
version: '3.1'
services:
  db:
    image: postgres:13
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
    ports:
      - "5432:5432"
```

Antes de hacerle el compose up comprobamos si el postgresql está utilizando el puerto con
``` sudo netstat -putan ```

![1](https://user-images.githubusercontent.com/91197967/212317614-2cbaac49-b115-4289-8601-58d8b2169d70.png)

Vemos que el puerto está ocupado por un proceso de postgres asi que no podemos levantar nuestro contenedor.

Matamos el proceso: ```service postgresql stop```

Y comprobamos nuevamente con ``` sudo netstat -putan ``` que el proceso ya no aparece.

![2](https://user-images.githubusercontent.com/91197967/212318075-37e8eaf8-4b25-4722-9b64-0c2ae31ae1c4.png)

Ahora si levantaríamos nuestro contenedor ```docker-compose up```
y volvemos a comprobar que proceso está utilizando el puerto:
![3](https://user-images.githubusercontent.com/91197967/212318697-570d407d-30e1-42c9-914f-50f95d3ae88f.png)




