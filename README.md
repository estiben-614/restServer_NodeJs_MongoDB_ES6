#Webserver + RestServer + MongoDB + JWS + Google + Cloudinary

Bievenidos a mi RestServer usando ES6 (ES Modules)

Para las peticiones se recomienda leer la documentación del proyecto en POSTMAN donde se encontrará con mayor detalle cómo  realizar cada una de estas : 
``` https://documenter.getpostman.com/view/26573688/2s93Xzw2Sb#e02cc01e-e2b3-4a97-8b33-5e3bcb6f99e5```

Para ejecutar, primero instalar las dependencias de node usando  ```npm install ```

Luego, realice peticiones a la siguiente URL  ```http://localhost:8080```

Para crear un usuario,  use una petición POST a la dirección ```http://localhost:8080/api/usuarios``` con los siguientes datos en el body :                                                                                                       ``` {"nombre":"test1", 
                                                                              "google":true,
                                                                              "nuevoCampo":true,
                                                                              "correo":"test1@gmail.com",
                                                                              "password":"123456",
                                                                              "role":"ADMIN_ROLE"}```


 
Para crear un usuario con su información inicie sesión con su cuenta de Google desde ```http://localhost:8080```

Para ver todos los usuarios ingresados, use  las peticiones GET y que tienen los siguientes QUERY opcionales ```http://localhost:8080?desde=' '&limite= '   ' ```


Para hacer un login ingresar a ```http://localhost:8080/api/auth/login``` y realice una petición  POST con un usuario en su BD de la siguiente manera 
                                                                          ``` {"correo":"test20@gmail.com", 
                                                                             "password":"123456"}  ```
 . Se realizaran las correspondientes validaciones y si hay un login correcto se creará un JSONWEBSOCKET (JWS)

Para modificar y eliminar un usuario a partir de su ID, use  las peticiones PUT y DELETE ingresando el  parametro del ID  ```http://localhost:8080/<'type-userID-here>```.Adicional, para eliminar un usuario a partir de su ID primero debe autenticar un usuario (No el que se va a eliminar) y obtenga su JWS, luego realice la solicitud DELETE y agregue un header con el JWT  de la siguiente manera ``` x-token : < JWS_USER> ```. Una vez hecho lo anterior, el estado del usuario pasará de ```true``` a ```false``` indicando que fue eliminado

Para tener en cuenta, solo los usuarios con ```Role: ADMIN_ROLE,VENTAS_ROLE``` pueden realizar solicitudes DELETE

Adicional, se permite crear, actualizar, mostrar, y eliminar categorias de productos, y sus correspondientes productos, así como tambien permite realizar consultas de cada una de las colecciones de la BD

Por último, el webServer permite subir imagenes para cada producto o usuario a partir de su ID . Las imagenes pueden ser almacenadas de manera local o en Cloudinary

