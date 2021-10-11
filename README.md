<img src="http://drive.google.com/uc?export=view&id=1g1pcyHMPRAb13PgysLl5uDvVv2OhYPBG" align="right" />

# Practica MuleSoft 

### Jonatan Alejandro Castro Mejia

Guia de Uso e instalación de MuleSoft.

## A) Registro e Instalación

```markdown
1. Crear una cuenta en Mulesoft 
```

[En este link.](https://anypoint.mulesoft.com/login/signup?apintent=generic)

```markdown
2. Registrarse y Descargar Anypoint Studio (prueba gratuita por 30 dias)
```
[En este link.](https://www.mulesoft.com/lp/dl/studio)

```markdown
3. Descomprimir el archivo AnypointStudio-7.11.0-win64 (en mi caso para windows)
```

```markdown
4. Acceder a la carpeta resultante "AnypointStudio"
```

```markdown
5. Ejecutar el archivo "AnyPoint.exe"
```
```markdown
6. Elegimos la direccion del Workspace y Presionamos "Launch" 
```

<img src="http://drive.google.com/uc?export=view&id=1w2u03RyxMVkbLv6mBTM49hagf172BbO3" />  

## B) Creacion de un nuevo proyecto Mule
```markdown
1. Presionamos "Create a Mule Proyect"
```
![](nuevo.jpg)
```markdown
2. Ingresamos el nombre del proyecto, en mi caso "HelloMule" y presionamos "Finish"
```
![](nuevo1.jpg)

```markdown
Ahora nuestro entorno se modificara y apareceran elementos nuevos.
```
![](entorno.jpg)

```markdown
En la parte de Palette podemos arrastrar de los elementos que necesitemos, hasta el archivo que se encuentra abierto, en este caso el archivo es "hellomule.xml" 
```
![](palette.png)
```markdown
Arrastremos y soltemos el elemento "Listener" dentro del archivo
```
![](listener.jpg)
```markdown
Al hacer click en el circulo de Listener o en el icono de Listener
```
![](list1.png)
```markdown
Se abriran las opciones para el mismo 
```
![](opciones.png)
```markdown
Nos dirigimos a la seccion de Basic Settings y presionamos el Boton de @icon-plus, se abrirá la siguiente ventana:
```
![](config.png)
```markdown
Como podemos observar en esta ventana es donde podemos configurar la conexión, es decir:
* Asignarle un nombre
* Elegir que protocolo, 
* Definir el host 
* Definir el puerto 
En este caso no modificamos nada y simplemente presionamos "OK".
```
![](name_confing.png)
```markdown
Ahora veremos que el nombre que asignamos, aparece en el campo de "Connector configuration"
```

```markdown
Lo que sigue es definir la dirección o el "Path"
```

![](path.png)

```markdown
Este "Path" será un endpoint que ejecutará el flujo cuando el Listener la capte o la escuche 
```

```markdown
Ahora arrastramos y soltamos el elemento "Set Playload" dentro del flujo.
```
![](playload.png)

```markdown
 Se abrirán las opciones de Set Playload, modificaremos el valor de fx.
```

![](playconf.png)
* Presionamos el botón de fx e ingresamos la cadena "Hello Mule".

![](fx.png)

```markdown
Ahora guardaremos el proyecto presionando en la parte superior izquierda File y después Save o simplemente CTRL + S 
```

```markdown
Ahora ejecutaremos el proyecto dando click derecho en el flujo y presionamos " @icon-play Run proyect hellomule "

Si todo salio bien, obtendremos este resultado:
```
![](run.png)

```markdown
Ahora abriremos Postman o descargaremos MuleSofts Advanced REST Client para hacer una petición a nuestro endpoint

En mi caso yo usaré Postman

Haremos una petición POST con la direccion definida en el Listener (http://0.0.0.0:8081/hellomule)  
```

![](post.png)

```markdown
Al presionar "Send" la respuesta que obtendremos será:
```
![](res.png)

## Desplegar proyecto Mule en CloudHub.

```markdown
1. Detenemos la ejecución del proyecto Mule, dando click derecho sobre el flujo y presionando "@icon-stop proyect hellomule"
```

![](1.png)

```markdown
2. Damos click derecho sobre el archivo hellomule.xml, luego en Anypoint Platform y seleccionamos Deploy to CloudHub.
```

```markdown
3. Nos pedira acceso ya que es por primera vez que tratamos de hacer deploy.
```
![](login.png)

```markdown
4. Una vez que accedemos, se abrirá una ventana como la siguiente:
```
![](cloud.png)

Observamos que en la parte superior izquierda tenemos un botón con leyenda "DESING", lo presionamos y cambiamos a SandBox

![](sand.png)

cambiamos a SandBox seleccionándolo y presionando "Switch"

```markdown
5. pasamos el cursor sobre el nombre de la aplicación
 * si este tiene @icon-times varificamos el error y lo trataremos de arreglar
 
 En mi caso el nombre del proyecto ya estaba en uso, por eso lo cambie a hellomule100

Esto es importante ya con errores no se podrá desplegar en CloudHub.
```

![](correct.png)

```markdown
6. Ahora presionamos "Deploy Application" y obtendremos la siguiente ventana:
```
![](dep.png)

```markdown
7. Presionamos "Open in Browser" y accedemos con nuestra cuenta
```

![](cuenta.png)

```markdown
8. Al acceder de forma satisfactorira se nos mostrará la siguiente pestaña, y al igual que antes, presionamos el botón de "Desing" y cambiamos a "Sandbox"
```
![](v1.png)

![](deployed.png)

```markdown
9. Ahora preisonamos el nombre del proyecto "hellomule100" y se nos redireccionará a otra pestaña.
```

![](domain.png)

En esta pestaña podremos ver, el dominio de nuestro proyecto ya desplegado en CloudHub.

En mi caso es 

[Este link](http://hellomule100.us-e2.cloudhub.io/)

Pero como recordaremos, para verificar la respuesta de la petición que creamos, es necesario acceder desde Postman (para hacer una petición POST)

![](deployedPost.png)

```markdown
10. Presionamos "Send"

Y verificamos la respuesta ¡Listo!
```
![](resp2.png)

# b) Como Configurar un endpoint con protocolo HTTPS en Anypoint Studio.

```markdown
1. Nos dirigimos a la carpeta src/main/resources y creamos un archivo(click derecho -> new -> File) con el nombre: local.properties

En este archivo "definiremos" las propiedades de una conexión con protocolo HTTPS

```

![](prop.png)

```markdown
2. Regresamos al archivo hellomule.xml tendremos lo siguiente
```

![](test.png)
```markdown
3. Seleccionamos HTTP_Listener_config, 
    * Presionamos Edit
    * Cambiamos el protocolo por HTTPS y
    * Modificamos el puerto por $(https.port)
```
![](changeport.png)

```markdown
4. Probamos la conexión y veremos que esta fallará, ya que hay que agregar una configuración global para la conexión. (si continua fallando no hacer el archivo local.properties y simplemente cambiar de puerto a 8082)
```
![](testconexion.png)

```markdown
5. Cerramos las ventanas de prueba de conexión y de edición de la conexión y regresamos al archivo hellomule.xml
```
![](reg.png)

```markdown
6. Presionamos "Create" 
```
![](global.png)

Global Configurations -> Configuration properties

![](global1.png)

```markdown
7. Seleccionamos el archivo que creamos (local.properties) y presionamos "OK"
```
![](local.png) @icon-arrow-right
![](local2.png)
Presionamos "OK"

Y ahora tendremos otro elemento 

![](elem.png)

```markdown
8. Regresamos al archivo hellomule.xml, seleccionamos HTTP_listener_config y presionamos edit 
```

```markdown
9. Nos dirigimos a la pestaña TLS y cambiaremos la configuracion TLS (de none a EditInline)

Para eso crearemos un archivo keystore (jks)
```
![](tls.png)
```markdown
10. Abriremos una terminal 

11. Escribimos los siguientes comandos

cd \  ------------------------(para colocarnos en c: )
dir /b/s keytool.exe ---------(para buscar el archivo ejecutable keytool.exe)

```
Para una guia completa seguir este [mini tutorial](https://support.code42.com/Administrator/6/Configuring/Install_a_CA-signed_SSL_certificate_for_HTTPS_console_access)

Usaremos el de java.

![](java.png)


```markdown
12. Escribimos el comando 
PATH=%PATH%;C:\Program Files\Java\jdk-15.0.2\bin 

En mi caso tengo una version de java relativamente reciente, pero puede usar alguna anterior también.
```
```markdown
13. Escribimos el comando cd \Users\<yourusername>
(cambia yourusername por tu nombre de usuario) 
```
```markdown
14. Ahora escribimos el siguiente comando 

keytool -genkey -alias <key-alias> -keystore <keystore-name>.jks -keyalg RSA -storetype JKS

los elementos dentro de <> los puedes modificar a tu placer.
```
![](jks.png)
```markdown
Y finalmente obtendremos un archivo .jks dentro de la carpeta \Users\<yourusername>.
```

```markdown
15. Ahora hay que mover el archivo.jks a la carpeta src/main/resources dentro del proyecto
```
![](mover.png)

```markdown
16. Regresamos a configurar TLS del Listener. 

En TLS Configuration cambiamos de None a Edit Inline y nos aparecerán los campos para configurar TLS.
```
![](lis3.png)

![](gloabaltls.png)

```markdown
17. Dentro de los campos de Key Store Configuration agregaremos 

* En Path el nombre del archivo que generamos y copiamos a la carpeta src/main/resources 
* El alias que proporcionamos via terminal (en mi caso key-alias)
* Y el password (en mi caso password)
```

![](tlsconfig.png)

```markdown
18. Probamos la conexión.
```

![](success.png)

Y ¡Listo! la conexión ahora tendrá un protocolo HTTPS 

```markdown
19. Probemos la conexión en Postman (ejecutando el proyecto en Anypoint Studio antes) Verificamos que en la configuracion de Postman
```
![](pos3.png)

esta opción este desactivada

![](post4.png)

Ahora ingresamos a https://0.0.0.0:8082/hellomule

![](post2.png)

damos Click en Send

![](post5.png)

y vemos que la respuesta es correcta para ese endpoint.

¡Listo! Terminamos de verificar que la conexión ahora tiene protocolo https.


# C) ¿Cómo configurar un protocolo HTTPS para todos los endpoints? (De forma global y no para cada uno)

```markdown 
1. Abrimos nuestro archivo local.properties con Mule Properties Editor.

2. ingresamos lo siguiente:

salesforceUsername=<yourUsername>
salesforcePassword=<yourPassword>

<> debes de modificarlo con tus datos que refistraste anteriormente

```

[link con guía de instalación de Mule Properties Editor](https://mulesy.com/adding-secure-property-plugin-or-editor/)

```markdown 
4. Ahora dentro de la paleta presionamos la opción "Search in Exchange", se abrirá una ventana como la siguiente:
```
![](search.png)

```markdown
5. Buscamos Mule Secure Configuration Property Extension, la seleccionamos y presionamos Add> y despues Finish
```
![](add.png)

```markdown
6. Veremos que se agregara a los elementos dentro la Paleta de mule y en los paquetes
```

![](secure.png)
![](secure2.png)

```markdown
7. Ahora nos dirigimos a la sección de elementos globales, presionamos el botón de create 
```
![](globale.png)

```markdown
8. Escribimos la palabra global y Seleccionamos la opción "Global Property" y Presionamos "OK"
```
![](global2.png)

```markdown
9. Ahora se abrira una ventana como la siguiente:
```
![](securekey.png)



```markdown
10. Aqui ingresaremos los algunos datos que tendremos que recordar 

Por ejemplo yo agregue: 

* Name : secure-key
* Value: MulesoftValue

Y presionamos "OK"
```
![](datos.png)

Ahora será un elemento global

![](global3.png)

```markdown
11. Preisonamos el botón de Create y buscamos "Secure Properties Config", lo seleccionamos y presionamos "OK"
```

![](secureconf.png)


Se abrirá la siguiente ventana: 

![](secureconf2.png)

```markdown
12. Llenamos los campos (o seleccionamos)

* File
* Key
* Algorithm


```
![](secureconf3.png)

Y presionamos "OK"

```markdown
13. Ahora buscaremos una dependencia para agregarla a los elementos de la paleta, esta será "Salesforce Connector" lo agregamos y presionamos "Finish"
```
![](sales.png)

Anteriormente definimos una respuesta con Set Playload, y ahora lo que haremos es cambiarlo por un elemento de Salesforce, en este caso lo cambiaremos por un elemento "Create"

![](playload.png)

![](create.png)

```markdown
14. Reemplazamos Set Playload con Create.
```
![](create2.png)

```markdown
15. Presionamos el elemento Create dentro del flujo y aparecera su configuración.
```
![](createconf.png)

```markdown
16. Presionamos el botón @icon-plus dentro de Basic Settings, se abrirá una ventana y agregaremos los siguientes datos: 

En Username: $(secure::salesforceUserName)
En Password: $(secure::salesforcePassword)

Y presionamos "OK"
```
![](salesconfig.png)

```markdown
17. Después en la cofiguración de Create, en la Sección General modificamos lo siguiente:

* Type: lead
* Records:

%dw 2.0
output application/json
---
[{
	FirstName: "Max",
	LastName: "Mule",
	Email: "maxthemule@mulesoft.com",
	Company: "MuleSoft"
}]
```

```markdown
18. nos dirijimos al archivo local.properties y damos doble click en salesforceUserName, después damos click en encrypt
```

![](mulesoftvalue.png)

Se mostrará una ventana con dos campos, una para elegir un algoritmo de encriptación y la llave que definimos en el paso **10**, al precionar "OK"
regresaremos y veremos que el username ahora estará encriptado, presionamos "OK"

![](encriptado1.png)

```markdown
19. Repetimos con el password.
```

![](encriptado2.png)

```markdown
20. Ahora hay que desplegar el proyecto en CloudHub, Agregando el nombre y la llave de seguridad del paso 10.
```

![](cloud2.png)

ya en el navegador, podremos observar que se actualizo!

![](act.png)

# D) Crear una API en API Manager de Anypoint Platform.

```markdown
1. Ingresamos a Anypoint Platform desde este link

https://anypoint.mulesoft.com/home/organizations/31352752-2086-43f9-8ce2-d191f56d13f2/
```
![](platform.png)

Presionamos "Start designing"

```markdown
2. Presionamos Manage API 
```
![](api.png)

```markdown
3. Seleccionamos "Create new API"
```
![](new.png)    

Podemos usar lo siguiente: 

![](newapicreated.png)

```markdown
4. La API estará lista cuando aparezca la siguiente pestaña: 
```

![](api1.png)

```markdown
5. Ahora regresamos a Anypoint Studio y configuramos un nuevo tipo global, dando Click en Global Elements -> Create -> Component Configurations ->API Autodiscovery
```

![](globale.png) 

```markdown
6. Copiamos el id de Autodiscovery que fue generado cuando creamos la API en Anypoint Plantform.
```

![](id.png)

```markdown
7. Pegamos el id en el campo de API id, seleccionamos el flujoy presionamos "OK"
```

![](cid.png)

```markdown
8. Ahora regresemos a Anypoint Platform, en la parte de API Administration entremos a ver la información del entorno, dando click en el botón señalado.
```

![](info.png)

```markdown
9. Copiamos los datos señalados a continuanción:
```

![](se.png)

y lo agregamos a las properties cuando hagamos el deploy a CloudHub, usando:

```markdown

* anypoint.platform.client_id
* anypoint.platform.client_secret

```

![](prop2.png)

Damos click en Deploy Application y esperamos a que el status cambie a Started, lo que significará que se desplego de manera correcta. ¡Listo!

![](deployed2.png)

# E) Mejores prácticas de diseño de APIS 

```markdown
Antes de empezar hay que tener varios conceptos muy claros.

1. Métodos HTTP:
Se Usan para hacer consultas a una API

    * GET: Obtener datos
    * POST : Guardar Datos
    * PATCH : Actualizar parcialmente los datos de una instancia.
    * PUT : Actualizar completamente la instancia.
    * DELETE : Eliminar una instancia.
    
2. Códigos de estado:
Se usan para dar información acerca del estado de la petición: 

    1. Respuestas informativas (100–199),
    2. Respuestas satisfactorias (200–299),
    3. Redirecciones (300–399),
    4. Errores de los clientes (400–499),
    5. errores de los servidores (500–599).

3. Parámetros de consulta:
Se utilizan dentro de una consulta para usar o consultar uno o varios valores especificos.

Su estructura es: 

    * /users?fields=name
    
    Después de el signo de interrogación, se encuentran "variables" que tienen un valor.
    Por ejemplo fields tiene a name como valor.
    
```

```markdown
1. Creamos una nueva API en Anypoint Platform usando Desing Center.
Presionamos el botón @icon-plusCreate new
```
![](desing.png)

```markdown
2. Seleccionamos "New API Spec" 
```
![](spec.png)

```markdown
3. Ingresamos el nombre de la API y Presionamos Create API Spec
```
![](newapi2.png)

```markdown
4. Ahora veremos nuestro "directorio principal" con un archivo RAML 
```

![](spec2.png)

```markdown
5. Creamos un nuevo archivo, presionando el botón @icon-plus, con el nombre library.raml
```
![](newa.png)

![](newa2.png) 

y presionamos create.

```markdown
Ahora el archivo aparecerá con los demás.
```

![](newa3.png)

```markdown
6. Copiamos y pegamos el siguiente código dentro del archivo library.raml
```

```RAML
#%RAML 1.0 Library
usage:
types:
 Text: !include dataTypes/dataType.raml
resourceTypes:
 text:
   post:
     description: This API will send a secure text message with Twilio to the phone number you input
     body: Text
     responses:
       200:
         body: Text
       400:
       401:
       500:

```
La variable *Text* hace referencia a la estructura que definimos dentro del archivo dataType.raml (SMS)

La variable *text* hace referencia a el tipo de método HTTP que se usará para realizar una petición futura.

dentro de *text* podemos observar que tenemos la sección para las respuestas (response) en donde tenemos varios códigos de estado, y solo regresaremos la estructura de SMS cuando tengamos un estado 200, es decir cuando la petición sea correcta, en otro caso, no haremos nada. 

```markdown
7. Ahora creamos un carpeta al que llamaremos dataTypes y dentro de esta carpeta crearemos un nuevo archivo que se llamará dataTypes.raml

Agregaremos el siguiente código en el archivo dataTypes.raml
```

```markdown
Este archivo define lo siguiente

    * El número al que mandaremos un mensaje 
    * El mensaje
    
También define la estructura y los tipos de cada "Objeto" y un pequeño ejemplo

```

```raml
#%RAML 1.0 DataType
properties:
 ToPhoneNumber:
   description: Enter the mobile number to send a text
   example: 15553334444
   type: integer
   required: true
 Message:
   description: Enter your message
   example: Text message body
   type: string
   required: true
```

una vez agregado el código, se mostrará una vista previa de lo que agregamos. 

![](previa.png)

```markdown
8. Ahora regresamos al archivo raiz (een mi caso sendsmsapi100.raml)
y escribimos lo siguiente: 
```

```raml
mediaType: application/json
uses:
 library: library.raml
/text:
  type: library.text
```
Con este código hacemos referencia al archivo library.raml

```raml
uses:
 library: library.raml
```

y con este otro código desde el archivo library.raml usamos los tipos de datos o la estructura de los datos desde el archivo dataType.raml

```raml
/text:
  type: library.text
```
y /text lo podemos ver como un endpoint 


```markdown
Recapitulando

* Definimos la estructura de un SMS, con destinatario y con un mensaje

* Definimos la forma en como se enviarán los SMS (mediante un método POST, el cual fue definido en el archivo library.raml)

* Definimos un endpoint usando la conexión entre el archivo library.raml y dataType.raml

```
![](endp.png)

```markdown
9. Definir un entorno seguro para realizar peticiones.

Crearemos un archivo al que llamremos securityScheme.raml
Copiamos y pegamos el siguiente código dentro del mismo.

```

```raml
#%RAML 1.0 SecurityScheme
type: Basic Authentication
describedBy:
 headers:
   client_id:
     type: string
   client_secret:
     type: string
 responses:
   401:
     description: Unauthorized or invalid client application credentials
   500:
     description: Bad response from authorization server, or WSDL SOAP Fault error
```

Este código será de rgan ayuda ya que dentro de los header pediremos datos de seguridad como lo son el *id de cliente* y *cliente secreto* y sin esos datos no será posible obtener o modificar ningun dato de la API.

```markown
10. Ahora agregamos el siguiente código en nuestro archivo library.raml dentro de *usage* para incluir lo especificado en el archivo securityScheme.raml
```
![](usage.png)

```markdown
11. Abrimos nuestro archivo raiz y copiamos y pegamos el siguiente código justo debajo del titulo
```
![](usage1.png)

Esto es de utilidad ya que así la API tendrá **Basic Authentication security** y por ende el usuario que haga una petición tendrá que agregar a los headers el client_id y el client_secret.

```markdown 
12. publicamos to exchange para poder manipular la API desde Anypoint Studio, hacemos click en el botón Publish y luego Publish to Exchange.
```


![](exchange.png)
Agregamos los datos que se requieren, y presionamos Publish to Exchange.
![](publish.png)
Ahora ya esta publicado en Exchange.
![](listo.png)

Lo podemos verificar en la parte de Exchange @icon-check

![](ex.png)

```markdown 
13. Ahora Abrimos Anypoint Studio para importar nuestra API.

Necesitamos crear un nuevo proyecto para esto, cuando lo estemos creando nos movemos a la sección de import y presionamos el icono de @icon-plus,
nos aparecerá una venta para agregar la dependencia.

En el campo de busqueda ingresaremos el nombre de nuestra API que desplegamos en Exchange, presionamos Add y luego Finish.
```

![](import.png)

Con lo siguiente sabremos que se importo correctamente: 

![](corr.png)

```markdown
14. Bajamos y en el siguiente elemento agregaremos un Listener: 
```
![](agregar.png)