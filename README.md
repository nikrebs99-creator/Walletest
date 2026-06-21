# Walletest
Testing my new skills learning html, css, bootstrap, js and jquery!
Documentación alkemy wallet




Proyecto desarrollado por Nicolás Krebs respecto a lo visto en el módulo 2 del curso Full Stack Java Trainee.
















INDICE


index.html	5
registro.html	6
menu.html	7
deposit.html	8
sendmoney.html	9
transactions.html	10
style.css	11
utilidades.js	12

Introducción
Sería falso afirmar que el contenido es de mi completa autoría, pues para el avance, desarrollo y aprendizaje de este proyecto, me apoyé en gemini como tutor para que me guiara en el paso a paso de lo que tenía en mente desarrollar.
La conversación completa se puede encontrar en el siguiente enlace
https://gemini.google.com/share/fe6fb01b6d9f
Para esto, se creó una “gema”, o una “IA con personalidad” a la que se le indicó que su función sería cumplir un rol de docente y explicara código de forma pedagógica para ayudar al entendimiento y comprensión de cada parte del código.

Esta “gema” fue usada desde la creación de la billetera en la L4 en adelante, por lo que se puede ver un crecimiento en el nivel de las preguntas, deducciones, planteamientos y solicitudes.

A lo largo de todo el código, se pueden ver comentarios <!-- –>  para guiarme dentro de html, // // dentro de javascript y /* */ dentro de css. Estos comentarios tienen la finalidad de ir guiándome por los documentos, algunos como recordatorio de que es lo que hacen algunas lineas, y otros como explicaciones para no olvidar cómo funcionan las cosas. Algunos con un giro cómico, porque de alguna manera y otra me divertí en este pequeño proyecto.
Para ser añadido al portafolio, sin embargo, borraré aquellos comentarios para dar un aire de formalidad; espero que ud se divierta con los comentarios y hacer un poco menos tediosa la evaluación.
Este trabajo es realizado con Bootstrap 4 para un correcto uso de jquery.



















Archivos
Todos los archivos siguen una misma temática de colores, con un enfoque en responsividad y Mobile first! Además de tener un reloj funcional en el footer. Para todas las páginas, existen modales personalizados únicos para cada posible “error” de usuario que pude imaginar. Lo primero es intentar pasar de log-in sin logear; se le menciona al usuario que debe entrar con correo y contraseña y redirige el usuario a index.html. 
Todo archivo encuentra sus scripts encapsulados en un document.ready con el fin de que no queden funciones a medio cargar debido a la rapidez de un usuario intrépido.



































index.html
Pantalla de log-in, 
Crea usuarios iniciales en localstorage, para poder testear, y no estar vacío en su totalidad.
Chequea que email/contraseña estén en localstorage
Da la opción de entrar a Registro
Posee un icono de pregunta por si el usuario no está seguro de que hace un botón.


registro.html
Permite la creación de nuevos usuarios con email y contraseña.
Con regex se revisa que el correo tenga formato tipo “TEXTO @ TEXTO . ALGO”
Se revisa que el correo no esté ya en localstorage para evitar duplicados.
Se revisa que ambos campos tengan carácteres en el formulario
Se crea la cuenta añadiendo a localstorage










menu.html
Menú donde el usuario puede depositar, enviar dinero, o dirigirse a ver el historial de transacciones.
Se muestra un mensaje de bienvenida a usuario@correo.com
Se muestra el saldo actual del correo activo
Depositar mueve al usuario a deposit.html
Enviar dinero mueve al usuario a sendmoney.html
Últimos Movimientos mueve el usuario a transactions.html
se permite volver a la pantalla de logueo con Cerrar sesión (lleva a index.html).

(saldo ficticio inicial)









deposit.html
Formulario donde el usuario puede añadir fondos a su cuenta bancaria.
Campo donde se revisa que el número ingresado sea un número positivo mayor a 0.
se permite volver a menu.html sin añadir fondos.















sendmoney.html
Cada usuario activo tiene una lista de contactos (guardado como lista) en localstorage. Se debe seleccionar un contacto para poder enviar dinero.
Formulario para agregar contactos a enviar dinero
Lista de contactos, con la opción de borrar o seleccionar
Seleccionado el usuario, se permite recién hacer una transferencia de dinero con un número positivo mayor que 0
Realizada la transferencia, se devuelve al usuario a menu.html con el valor descontado del saldo anterior y se registra la resta en una lista historial en localstorage.
Se permite la vuelta a menu.html sin haber realizado modificaciones


transactions.html
Historial de movimientos de cada usuario, parámetro también guardado en localstorage.
Permite ver al usuario la lista de movimientos asociados a su correo electrónico
Se permite filtrar los movimientos por depósitos o transferencias, y ver sólo uno de aquellos en pantalla.
Se permite la vuelta a menu.html



style.css
Contiene detalles sobre el estilo global de Alke wallet, con enfoque móvil y responsividad.
Un fondo en degradé morado, con contenedores tipo cristal difuminado y sombreado al fondo y espacio en los bordes de la pantalla. 
Se define body para ser aplicado en todas los html donde style.css se invoque con link.
Se busca que todo container tenga el mismo estilo mencionado anteriormente, se define.
sendmoney.html tiene un override de container dado que es la única página que ocupa más de un container y requiere que todos sean distintos. En un futuro, definir distintos container (container1, container2, etc) está contemplado, en caso de expandir la billetera y requerir de más cuadros.
























utilidades.js
Contiene funciones con javascript, utilizadas para “inyectar” código globalmente como lo es el uso de modales (ventanas pop-up estilizadas), un footer dinámico que puede editarse fácilmente de ser necesario y un reloj que se actualiza cada 1 segundo.
function cargarModal() Inyecta el div de id “modalGlobal” en toda página donde utilidades.js sea cargado, facilitando su uso y modificación para uso posterior
window.mostrarMensaje establece el uso de ventanas como nuevos pop-up
si la página no ha tenido tiempo de cargar cargarModal() en el archivo, fuerza la implementación del mismo, para que no hayan llamadas vacías ni errores debido a funciones no implementadas.
Se implementa el modal por defecto siendo “info” y no derivando a ningún urlDestino, junto con dos modales extra tipo “error” y “éxito”, cambiando cada uno sus atributos estílísticos en cada modal.
cargarFooter inyecta el footer en cada página con utilidades.js cargado, para facilitar su edición y funcionamiento.
function actualizarReloj() se encarga de actualizar el reloj del footer cada segundo, para que el usuario no pierda rastro del tiempo mientras se encuentra en linea.
