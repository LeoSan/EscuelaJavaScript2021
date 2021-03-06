# 12 Curso de Asincronismo con JavaScript

Este nivel es sobre nuevas funciones e implementacones de ECMAScript 5-6-7 

## Clase 1: Bienvenida 
- Profesor Oscar Barajas Tavares  @gdnx 

## Clase 2: Qu茅 es el asincronismo? 
> JavaScript es sincrono y no bloqueante, con un bucle de eventos (concurrente), implementado con un 煤nico hilo para sus interfaces de entrada y salida.  

- 馃У Thread: Thread para Javascript permite realizar programaci贸n multihilos en este entorno. En realidad, simula la creaci贸n y ejecuci贸n de hilos, pero para el desarrollador es lo mismo. 脡sto simplifica much铆simo la creaci贸n de aplicaciones Javascript.
- 馃毇 Bloqueante: Una llamada u operaci贸n bloqueante no devuelve el control a la aplicaci贸n hasta que se ha completado. Por tanto el thread queda bloqueado en estado de espera.
- 馃毧 No bloqueante: Una tarea no bloqueante se devuelve inmediatamente con independencia del resultado. Si se complet贸, devuelve los datos. Si no, un error.
- 馃帪锔? S铆ncrono: Las tareas se ejecutan de forma secuencial, se debe esperar a que se complete para continuar con la siguiente tarea.
- 馃殾 As铆ncrono: Las tareas pueden ser realizadas m谩s tarde, lo que hace posible que una respuesta sea procesada en diferido. La finalizaci贸n de la operaci贸n I/O (entrada/salida) se se帽aliza m谩s tarde, mediante un mecanismo espec铆fico como por ejemplo un callback, una promesa o un evento, lo que hace posible que la respuesta sea procesada en diferido.
- 馃洡锔? Paralelismo: El paralelismo es la ejecuci贸n simult谩nea de dos o m谩s tareas. Algunas tareas se pueden dividir en partes m谩s peque帽as que pueden ser resueltas simult谩neamente.
- 馃幃 Concurrencia: La concurrencia es la capacidad de un algoritmo o programa para ejecutar m谩s de una tarea a la vez. El concepto es similar al procesamiento paralelo, pero con la posibilidad de que muchos trabajos independientes hagan diferentes cosas a la vez en lugar de ejecutar el mismo trabajo.
- 馃寑 Eventloop o Loop de eventos: El bucle de eventos es un patr贸n de dise帽o que espera y distribuye eventos o mensajes en un programa.


### 馃摑 Formas de manejar la asincron铆a en JavaScript:

- 馃摡 Callbacks: Una funci贸n que se pasa como argumento de otra funci贸n y que ser谩 invocada.
- 馃馃徏鈥嶐煫拆煆? Promesas: (implementado en ES6) Una promesa es una funci贸n no-bloqueante y as铆ncrona la cual puede retornar un valor ahora, en el futuro o nunca.
- 馃洠锔? Async / Await: (implementado en ES2017) Permite estructurar una funci贸n asincr贸nica sin bloqueo de una manera similar a una funci贸n sincr贸nica ordinaria.
- 馃搶 En JavaScript casi todas las operaciones de I/O (Entrada y Salida) no se bloquean. A esto se le conoce como as铆ncronismo. Lo 煤nico que no es procesado antes de que termine la operaci贸n son los callbacks, ya que 茅stos est谩n amarrados a una operaci贸n y esperan a que sea finalizada para poder ejecutarse.
- 鈴? El asincronismo es una manera de aprovechar el tiempo y los recursos de la aplicaci贸n, ejecutando tareas y procesos mientras otros son resueltos en background (como la llegada de la informaci贸n de una API), para posteriormente continuar con las tareas que requer铆an esa informaci贸n que no ten铆as de manera instant谩nea.
- 鈴诧笍 Un ejemplo f谩cil de asincronismo vs sincronismo es invitar a unos amigos a una fiesta y ofrecer una parrillada. Primero decides colocar la carne y verduras a la parrilla y luego repartir bebidas y algo para picar (snacks). Si fuera una persona s铆ncrona (Blocking) tendr铆as que esperar a que la comida de la parrilla est茅 cocinada y luego atender a los invitados. Pero si fuera una persona as铆ncrona (Non Blocking) luego de poner la carne al carb贸n, sacas las bebidas fr铆as de la nevera y compartes con los invitados mientras se cocina la carne. La acci贸n de que la comida en la parrillada est茅 lista ser铆a un callback que est谩 esperando que finalice el proceso para ejecutarse. Pero otros procesos (como compartir la velada con bebidas y algo de picar) ya podr铆an irse realizando.

**Cuando preguntan si JavaScript es multi-hilo y as铆ncrono**
![Meme](info/meme.png)

## Mas Datos
- https://www.youtube.com/watch?v=bWvnWhVCHAc
- https://platzi.com/clases/examen/25b3f72b-3f80-47a5-9913-d1e6e8f37641/examen_usuario/
  

## Clase 3: Event Loop? 
>  El bucle de eventos es un patr贸n de dise帽o que espera y distribuye eventos o mensajes en un programa.

Para entender el Event Loop, en el siguiente GIF 


![Explicaci贸n](info/eventLoop2.gif)

Se muestra que la primera tarea asignada (mostrar por Consola la palabra: 鈥渟tart鈥?) pasa por el Call Stack luego se imprime en consola. Cuando el Call Stack tiene el 鈥渟etTimeout鈥? se debe esperar un periodo de tiempo en este caso 5 segundos para imprimir el mensaje: 鈥淐allback Function鈥?, ah铆 es cuando vemos en Web APIs el timer. Mientras tanto, el c贸digo sigue corriendo a la siguiente tarea para imprimir en consola la palabra: 鈥渆nd鈥?.
.

El Event Loop es la tarea asignada (en este ejemplo el 鈥渃allbackFn()鈥?) para mover del Task Queue al Stack, solo si el stack est谩 vac铆o:


## Javascript se organiza usando las siguientes estructuras de datos:

- 馃梼锔? Memory Heap: Regi贸n de memoria libre de gran tama帽o, dedicada al alojamiento din谩mico de objetos (asignado a un mont铆culo). Es compartida por todo el programa y controlada por un recolector de basura que se encarga de liberar aquello que no se necesita, es decir de forma desorganizada se guarda informaci贸n de las variables y del scope.

![Ciclo ](info/Ciclo.png)

- 馃攱 Call Stack (pila LIFO: Last-in, First-out): Apila de forma organizada las instrucciones de nuestro programa. La pila de llamadas, se encarga de albergar las instrucciones que deben ejecutarse. Nos indica en que punto del programa estamos, por donde vamos.


-馃殫馃殨馃殭 Task Queue (cola): Cada vez que nuestro programa recibe una notificaci贸n del exterior o de otro contexto distinto al de la aplicaci贸n, el mensaje se inserta en una cola de mensajes pendientes y se registra su callback correspondiente. El stack debe estar vac铆o para que esto suceda.

- 馃殫馃殨 Micro Task Queue: Aqu铆 se agregan las promesas. Esta Queue es la que tiene mayor prioridad.

## Ejemplo

![EventLoop](info/EventLoop.gif)


## Enlace 
- http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D

## Clase 4- 5 : Event Loop? 

- Web APIs JavaScript del lado del cliente: setTimeout, XMLHttpRequest, File Reader, DOM. Node: fs, https.

- API: El t茅rmino API es una abreviatura de 鈥淎pplication Programming Interface鈥? (Interfaz de programaci贸n de aplicaciones en espa帽ol). Es un conjunto de rutinas que provee acceso a funciones de un determinado software.

- Hoisting: Sugiere que las declaraciones de variables y funciones son f铆sicamente movidas al comienzo del c贸digo en tiempo de compilaci贸n.

- XML: Lenguaje de marcado creado para la transferencia de informaci贸n, legible tanto para seres humanos como para aplicaciones inform谩ticas, y basado en una sencillez extrema y una r铆gida sintaxis. As铆 como el HTML estaba basado y era un subconjunto de SGML, la reformulaci贸n del primero bajo la sintaxis de XML dio lugar al XHTML; XHTML es, por tanto, un subconjunto de XML.

- DOM: El DOM permite acceder y manipular las p谩ginas XHTML como si fueran documentos XML. De hecho, DOM se dise帽贸 originalmente para manipular de forma sencilla los documentos XML.
Events: Comportamientos del usuario que interact煤a con una p谩gina que pueden detectarse para lanzar una acci贸n, como por ejemplo que el usuario haga click en un elemento (onclick), que elija una opci贸n de un desplegable (onselect), que pase el rat贸n sobre un objeto (onmouseover), etc.

- Compilar: Compilar es generar c贸digo ejecutable por una m谩quina, que puede ser f铆sica o abstracta como la m谩quina virtual de Java.

- Transpilar: Transpilar es generar a partir de c贸digo en un lenguaje c贸digo en otro lenguaje. Es decir, un programa produce otro programa en otro lenguaje cuyo comportamiento es el mismo que el original.

## clase 6 : Qu茅 son los Callbacks

- 馃摡 Callbacks: Una funci贸n que se pasa como argumento de otra funci贸n y que ser谩 invocada.


## clase 7 : Tipo de llamado para consumir API forma -> XMLHTTPRequest

>  XMLHttpRequest es un objeto de JS que permite hacer peticiones hacia servicios en la nube(URLs o APIs).

**Existen 5 estados en un llamado XMLHttpRequest:**
- 0 鈫? Se ha inicializado.
- 1 鈫? Loading (cargando).
- 2 鈫? Se ha cargado.
- 3 鈫? Procesamiento si existe alguna descarga.
- 4 鈫? Completado.

```
if (xhttp.readyState === 4) { // Me ayuda escuchar los estados para saber cuando estar谩 disponible la informaci贸n 

//Tu bloque 
} 
```
**M茅todos y propiedades:**

- xmlhttp.open() 鈫? Prepara la petici贸n para ser enviada tomando tres par谩metros: pr贸tocolo, url, as铆ncrono (true).
- xmlhttp.readyState 鈫? Retorna el estado de la petici贸n.
- xmlhttp.onreadystatechange 鈫? Un eventHandler que es llamado cuando la propiedad readyState cambia.
- xmlhttp.status 鈫? Retorna el estado de la respuesta de la petici贸n. (200,400,500)
- xmlhttp.send() 鈫? Env铆a la petici贸n.


**Caracter铆sticas del protocolo http:**

- Verbos: Los verbos indican acciones que est谩n asociadas a peticiones y recursos, es decir, sirven para la manipulaci贸n de recursos cliente/servidor. Los Verbos http son:

- GET 鈫? Solicita un recurso.
- HEAD 鈫? Solicita un recurso pero sin retornar informaci贸n, la estructura de esta petici贸n es igual que get tanto en su headers como estatus. Es 煤til cuando vamos a utilizar API, para comprobar si lo que vamos a enviar esta correcto y puede ser procesado.
- POST 鈫? Sirve para la creaci贸n de recursos en el servidor.
- PUT 鈫? Actualiza por completo un recurso, reemplaza todas las representaciones actuales del recurso de destino con la carga 煤til de la petici贸n.
- PATCH 鈫? Actualiza parcialmente un recurso.
- DELETE 鈫? Elimina un recurso.

**Los c贸digos de estados del servidor:**

> El c贸digo de estado (status codes) sirve para describir el estado de la petici贸n hecha al servidor.

- 1xx 鈫? Indican que la petici贸n fue recibida por el servidor, pero est谩 siendo procesada por el servidor.
- 2xx 鈫? Indican que la petici贸n fue recibida, aceptada y procesada correctamente.
- 3xx 鈫? Indican que hay que tomar acciones adicionales para completar la solicitud.
- 4xx 鈫? Indican errores del lado del cliente que hizo mal una solicitud.
- 5xx 鈫? Indican errores del servidor. Suelen aparecer cuando existe un fallo en la ejecuci贸n en el servidor.


**Los c贸digos m谩s comunes a la hora de interactuar con una API son:**


- 200 鈫? OK 鈫? Indica que todo est谩 correcto.
- 201 鈫? Created 鈫? Todo est谩 correcto cuando se hizo una solicitud POST, el recurso se cre贸 y se guard贸 correctamente.
- 204 鈫? No Content 鈫? Indica que la solicitud se complet贸 correctamente pero no devolvi贸 informaci贸n. Este es com煤n cuando se hacen peticiones con el verbo DELETE.
- 400 鈫? Bad Request 鈫? Indica que algo est谩 mal en la petici贸n (no encontr贸 algo).
- 401 鈫? Unauthorized 鈫? Significa que antes de hacer una solicitud al servidor nos debemos autenticar.
- 403 鈫? Forbidden 鈫? Indica que no tenemos acceso a ese recurso aunque se est茅 autenticado.
- 404 鈫? Not Found 鈫? Indica que no existe el recurso que se est谩 intentando acceder.
- 500 鈫? Internal Server Error 鈫? Indica que algo fall贸, es un error que retorna el servidor cuando la solicitud no pudo ser procesada.


## clase 8 : Tipo de llamado para consumir API forma -> Fetch data

>Para evitar la mala pr谩ctica de un Call Hell, no es recomendable exceder de 3 callback, para ello se utilizan las promesas o el Async Away.

> Existen varios tipos de console, dependiendo del navegador, la fuente o el color cambian de acuerdo al tipo

## 饾棖饾椆饾棶饾榾饾棽 #饾煹: 饾棖饾棶饾椆饾椆饾棷饾棶饾棸饾椄 饾椀饾棽饾椆饾椆 

> CallBacks Hell: Consiste en m煤ltiples Callbacks anidados que provocan que el c贸digo se vuelva dif铆cil de leer y 鈥榙ebuggear鈥? y por eso se debe evitar.

> forma de ejecutar comando desde consola claro si tiene node_module instalado 
> Ejemplo sintaxis [`node archivo.js`] ->  `node .\src\callback\challenge.js`
> Tambien recuerda que desde tu package.json en la secci贸n de script puedes anclar c贸digo para ejecutar Ejemplo 

![ejemplo](info/EjemploScript001.png)

![ejemplo](info/EjemploScript002.png)


## 饾棖饾椆饾棶饾榾饾棽 #饾煭饾煬: 饾棨饾槀茅 饾榾饾椉饾椈 饾椆饾棶饾榾 饾椊饾椏饾椉饾椇饾棽饾榾饾棶饾榾 


**Las promesas** 
- son as铆ncronas, por lo que el c贸digo continuar谩 su ejecuci贸n normalmente y luego dir谩 si la promesa se resolvi贸 o se rechaz贸. 
- Por lo que varias promesas pueden llegar a entrar en ejecuci贸n al mismo tiempo.

**Las promesas pueden suceder:**
- Ahora 
- En el futuro
- Nunca

**Para crear una promesa:**
- Utilizamos la palabra reservada new seguida de la palabra Promise que es el  constructor de la promesa. Este constructor recibe un 煤nico par谩metro que es una funci贸n, la cu谩l a su vez, recibe otros dos par谩metros: resolve y reject.

**Una Promesa puede estar en uno de los siguientes estados**
- Pendiente pending 鈫? Una promesa inicia en este estado: no cumplida, no rechazada:
Una promesa inicialmente est谩 pendiente.
- Cumplida fulfilled 鈫? Significa que la operaci贸n se complet贸 satisfactoriamente, .then(va => 鈥?)
Cuando llamamos a resolve entonces la promesa pasa a estar resuelta.
Cuando una promesa se resuelve entonces se ejecuta la funci贸n que pasamos al m茅todo .then
- Rechazada rejected 鈫? significa que la operaci贸n fall贸, .catch(err => 鈥?)
Si llamamos a reject pasa a estar rechazada (obtenemos un error que nos va a indicar la raz贸n del rechazo).
Si la promesa es rechazada entonces se ejecuta la funci贸n que pasamos a .catch

## 饾棖饾椆饾棶饾榾饾棽 #饾煭饾煭: 饾棛饾棽饾榿饾棸饾椀饾煭饾煭

- Por medio de Fetch se puede realizar peticiones HTTP as铆ncronas de JavaScript (JS) con promesas. La API Fetch proporciona una interfaz JS m谩s c贸moda para acceder y manipular; fetch() es un m茅todo global.

**Para poder usar fetch, primero tenemos que instalarlo**

Ir a la terminal e instalar fetch con: `npm i node-fetch`
Para poder compilar desde VSC, debemos registrar el modulo en package.json, abrimos el archivo y al final se agrega:

## 饾棖饾椆饾棶饾榾饾棽 #饾煭饾煯: 饾棛饾棽饾榿饾棸饾椀 饾棧饾棦饾棪饾棫 饾煭饾煯/饾煯饾煭 馃搨

**Repasando algunas de las caracter铆stica del protocolo http:**


> Los verbos indican acciones, est谩s acciones est谩n asociadas a peticiones y recursos. En l铆nea general sirve para la manipulaci贸n de recursos cliente/servidor. Los c贸digos de estados, los c贸digos son valores n煤meros que tienen un valor sem谩ntico.


**Algunos Verbos http son:**

- GET 鈫? Sirve para solicitar recurso.
- POST 鈫? Sirve para la creaci贸n de recursos en el servidor.
- PUT 鈫? Sirve actualizar por completo un recurso.
- DELETE 鈫? Sirve para eliminar un recurso.

**En el ejemplo de la clase se usa POST para guardar (enviar a la API) informaci贸n en lugar de obtener con GET (recibir).**

- Hay permisos que se deben tomar en cuenta para que el intercambio sea seguro, hay que especificar el modo (mode), aqu铆 se indica si se permite solicitudes de origen cruzado.

**驴Qu茅 es un origen cruzado?**

- CORS (Cross-Origin Resource Sharing) es un sistema, que consiste en transmitir encabezados HTTP , que determina si los navegadores bloquean el acceso del c贸digo JavaScript frontend a las respuestas para solicitudes de origen cruzado.

- La pol铆tica de seguridad del mismo origen proh铆be el acceso de or铆genes cruzados a los recursos. Pero CORS brinda a los servidores web la capacidad de decir que desean optar por permitir el acceso de origen cruzado a sus recursos. MDN

- Un origen tiene dominio/protocolo/puerto, un origen cruzado denominado 鈥淐ross  Origin鈥? es la palabra que se utiliza para denominar el tipo de peticiones que se realizan a un dominio diferente del dominio de origen desde donde se realiza la petici贸n.

- As铆 que si se coloca cors, indica que se permiten ciertas solicitudes predeterminadas de origen cruzado como GET y POST para salvaguardar y evitar manipulaciones maliciosas. 
- fuente -> https://javascript.info/fetch-crossorigin


## 饾棖饾椆饾棶饾榾饾棽 #饾煭饾煰: 饾棛饾槀饾椈饾棸饾椂饾椉饾椈饾棽饾榾 饾棶饾榾铆饾椈饾棸饾椏饾椉饾椈饾棶饾榾 饾煭饾煰/饾煯饾煭 馃帰

馃攣 **驴Qu茅 es una funci贸n as铆ncrona?**

> La declaraci贸n de funci贸n async define una funci贸n as铆ncrona que devuelve un objeto, lo cual permite a un programa correr una funci贸n sin congelar todo la compilaci贸n.

> Dada que la finalidad de las funciones async/await es simplificar el comportamiento del uso s铆ncrono de promesas, se hace m谩s f谩cil escribir promesas.

**La estructura se compone por las palabras reservadas async y await:**
- La palabra async antes de la funci贸n, hace que la funci贸n devuelva una promesa.
- La palabra await se utiliza dentro de las funciones async, lo que hace que el programa espere hasta que la variable(promesa) se resuelva para continuar.


**Resumen de metodos**
![Resumen](info/resumen-forma.png)


## Clase 饾煭饾煵: 饾棜饾棽饾椈饾棽饾椏饾棶饾榿饾椉饾椏饾榾 饾煭饾煵

> Un generador en JavaScript consta de una funci贸n generadora que muestra un objeto iterable Generator. 
> La palabra reservada yield se usa para pausar y reanudar una funci贸n generadora.

[Fuente](https://www.digitalocean.com/community/tutorials/understanding-generators-in-javascript-es)


`La estructura del Generador consta con la palabra function seguido de un aster铆sco * : function* 茅sta es una funci贸n generadora heredada.
El resultado que se quiere obtener se coloca al lado derecho de yield, puede ser de cualquier tipo (string, num茅rico, objetos, etc) y se puede tener tantos yield que se desee.`

## Ejemplo 

```
function* gen() {
    yield 1;
    yield 2;
    yield 3;
  }
  
  const g = gen();
  console.log(g.next().value);
  console.log(g.next().value);
  console.log(g.next().value);
```
```

//Uso de elementos en un solo bloque iterable 
(async () => {
  try {
    const videos = await fetchData(API);
    let view = `
    ${videos.items.map(video => `
      <div class="group relative">
        <div
          class="w-full bg-gray-200 aspect-w-1 aspect-h-1 rounded-md overflow-hidden group-hover:opacity-75 lg:aspect-none">
          <img src="${video.snippet.thumbnail.high.url}" alt="${video.snippet.description}" class="w-full">
        </div>
        <div class="mt-4 flex justify-between">
          <h3 class="text-sm text-gray-700">
            <span aria-hidden="true" class="absolute inset-0"></span>
            ${video.snippet.title}
          </h3>
        </div>
      </div>
    `).slice(0,4).join('')}

    `;
  } catch {
    console.log(error);
  }
})();
```


