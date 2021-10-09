# Practica MuleSoft 

### Jonatan Alejandro Castro Mejia

Guia de Uso e instalación de MuleSoft.

## Registro e Instalación

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

## Creacion de un nuevo proyecto Mule
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
Ahora lo que sigue es definir la dirección o el "Path"
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
* Presionamos el boton de fx e ingresamos la cadena "Hello Mule".

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

<img src="http://drive.google.com/uc?export=view&id=1g1pcyHMPRAb13PgysLl5uDvVv2OhYPBG" align="right" />













