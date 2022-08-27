# Flow-3

Este repositorio contiene el tercer ejercicio que consite en generar una página que despliegue la información de la hora

## Material necesario
Para poder realizar necesario es necesario tener instalado:
- [Node.js](https://github.com/nodesource/distributions/blob/master/README.md) Usar la versión LTS v16x e instalar los build tools.
- [Node-Red](https://nodered.org/docs/getting-started/local)
- Instalar dashboard, puedes consultar el como mediante la siguiente guía: [dashboard CodigoIoT](https://edu.codigoiot.com/mod/page/view.php?id=1080)

## Instrucciones

>No olvides primero abrir node red desde la terminal con node-red, de igual manera, abrir el **localhost:1880** en tu navegador de preferenecia

>Importar el flow 2, puedes encontrarlo dando click al siguiente enlace [Flow 2](https://github.com/ArathTzec/Segundo-Flow)

Se retomará el [Flow 2](https://github.com/ArathTzec/Segundo-Flow). El objetivo es desplegar la fecha en una interfaz gráfica. 

Da clic en el menú, ubicado en el botón de hamburguesa en la esquina superior derecha de la interfaz de Node-Red. Ahora da clic en Importar y después en Clipboard. Verás un cuadro de dialogo como el siguiente, pega el código json que respaldaste en la lección anterior.

Cambia la configuración del nodo inject para que el payload sea un timestamp que se repita cada 15 segundos: Agrega un nodo function y conecta la salida de inject a la entrada de function y la salida de function a la entrada de debug.

Ahora copia el siguiente código y pégalo en el cuadro de texto de las propiedades del nodo function. Éste código toma el mensaje enviado por el nodo inject en formato UNIX y lo convierte a un formato legible.

// Lo que está después de “//” son comentarios // Crea un objeto Date a partir del payload enviado por timestamp var date = new Date(msg.payload); // Cambia el payload para que sea una fecha con formato msg.payload = date.toString(); // Regresa el mensaje para que se envíe al sigueinte nodo return msg;

Si corres tu programa dando clic en Deploy; verás que cada 15 segundos da la fecha y hora en un lenguaje legible.

Para generar una página que despliegue la información de la hora, se ocupan los nodos de la sección dashboard, la cual contiene diversos nodos que te permiten configurar una interfaz gráfica. En éste ejemplo usarás el nodo text para mostrar la fecha.

Agrega un nodo text de la sección dashboard. Al agregarlo notarás que tiene un triángulo anaranjado encima, eso significa que no está configurado.

Al agregar un nodo de la sección dashboard verás que en el panel lateral -junto a las pestañas de info y debug- aparece una pestaña llamada dashboard.En ella configurarás la pestaña y los grupos de tu interfaz.

Selecciona la pestaña Layout, da clic en el botón +Tab, te aparecerá el elemento Tab1 en la lista de pestañas. Da clic en edit para configurar la pestaña.

Verás que se abre una ventana en la que se te permite editar el nombre y el ícono de tu pestaña. Dale el nombre que tú quieras (ej. Hora) y deja el ícono como dashboard. Da clic en Update cuando termines.

Ya que tienes creada la pestaña es momento de añadirle un grupo. En la lista de pestañas da clic en el botón + group que se encuentra junto a la pestaña que acabas de configurar

Te aparecerá un grupo nuevo debajo de la pestaña, da clic en el botón edit para abrir sus propiedades y configurarlo

Da clic en Update para terminar la configuración de la interfaz gráfica.

Da doble clic en el nodo Text para configurarlo

Para que text funcione necesitamos asignarle un grupo de interfaz gráfica (ui_group). Asígnale el que creaste en el paso anterior seleccionándolo de la lista si es que no lo tiene asignado por default.

Cambia el parámetro Label  de "text" a "La hora es:" (sin comillas). Esto hará que el encabezado del texto ahora sea "La hora es:".

El programa está listo, para hacerlo funcionar haz clic en Deploy. Ahora haz clic en la pestaña Dashboard y después en el icono que tiene una flecha saliendo de un cuadro. 


## Resultados
Una vez completados los pasos anteriores te dirigirá al Dashboard, que es la interfaz donde podrás ver la hora desplegada, esta cambiará cada 15 segundos cuando el nodo inject mande una hora nueva., como se ve en [Pantalla_Node-Red.png](https://github.com/ArathTzec/Flow-3/blob/main/Interfaz_Node-Red_Flow3.png) y [Pantalla_Node-Red.png](https://github.com/ArathTzec/Flow-3/blob/main/Conexiones_Node-Red_Flow_3.png) 