# 07 ¿Qué es React.js?

Este nivel es sobre nuevas funciones e implementacones de ECMAScript 5-6-7 

## Clase 1: Bienvenida 
- Profesor Oscar Barajas Tavares  @gdnx 

## Clase 2: ¿Qué es Next.js?


**Enlace**
- https://nextjs.org/docs


**Que es Next.js**
- Es un marco de desarrollo de código abierto construido sobre Node.js 
- Que permite funcionalidades de aplicaciones web basadas en React, 
- como la representación del lado del servidor y la generación de sitios web estáticos.

**Características principales de Next.js:**
- Facilidad para aprender
- Optimizado para SEO
- Posibilidad de combinar páginas estáticas junto a páginas dinámicas
- Compatibilidad con todos los recursos de React

**¿En qué consiste el Server Side Render?**

Para poder entender que es el Server Side Render, debemos entender como funcionan las aplicaciones React.js “normales”. Comunmente estas tienen un proceso para llegar al cliente y es el siguiente:

- Petición del sitio (Cuando el usuario llama al url de nuestro website)
- El servidor web como respuesta le manda un HTML inicial 💌
- El navegador recibe el HTML y lo comienza a leer línea por línea 👀, comúnmente tiene esta forma
- Llega a la etiqueta script, descarga en el navegador el archivo JS y comienza la magia de React.js ✨
- Toda la aplicación está dentro el div #root y el usuario ya puede ver e interactuar con el sitio

**Pero esto tiene 2 desventajas grandes:**

- SEO y rendimiento
- El buscador de google entra y revisa la primera respuesta, y solo encontrará el div vació, pero no te preocupes, ya que el mismo está entrenado para leer tu sitio, solo que lo hace más lento porque debe esperar a que el JS del script termine de cargar.

- Suponiendo que tienes miles y miles de páginas y únicamente 5 minutos para ser inspeccionado por el buscador. Tristemente, no todas las páginas serán leídas.

**Experiencia de usuario **
- Supongamos que tienes un usuario que está con su celular en medio de la nada y apenas tiene internet, entonces el mismo tendrá que esperar a que el sitio le mande el HTML, Encuentre el Script, descargue el mismo y lo renderice. Esto tomará mucho tiempo y quizás ya se abra ido a un sitio que cargue más rápido.
- 💪 La solución Para poder mejorar existen muchas estrategias, una de ellas es el Server Side Render, la principal diferencia está en el flujo el cual cambia a este:

- Petición del sitio (Cuando el usuario llama al url de nuestro website)
- El servidor web mediante una funcionalidad de React pre renderiza la aplicación, es decir sacar el HTML de los archivos React y lo pega a la futura respuesta del HTML
- El servidor web como respuesta le manda un HTML inicial 💌
- El navegador recibe el HTML y lo comienza a leer línea por línea 👀, y tendrá esta forma en este caso

> 💡 **Recuerda** Para que un website funcione siempre contará con un servidor para que lo mande al usuario, entonces por que no aprovechar el mismo para pasarle la tarea de renderizar contenido, Como frontends podemos olvidar que existe un servidor, ya que existen servicios como github pages que ya nos brindan un servidor para poder servir nuestros sitios con solo tener unos cuantos archivos HTML, CSS y JS.

> 📌 **RESUMEN:**  Next.js es un framework de React.js el cual te permite crear aplicaciones web   con mejor SEO y rendimiento, con una gran facilidad a nivel de configuración. Este framework puede crear aplicaciones hibridas, es decir que tendra tanto paginas estaticas como paginas las cuales implementarán server side render.

## Clase 3: Primeros pasos en Next.js

- Paso 1: Preparando el proyecto, Creamos una nueva carpeta donde estará nuestro proyecto
- Paso 2: Corremos el comando `npx create-next-app appName` ó `npx create-next-app@latest --ts appName` para crear componer nuestra aplicacion con next, es parecido al comando npx create-react-app appName
- Paso 3: Una vez listo todo nos presenta la siguiente estructura de archivos

![Estructura](./info/preparacion.png)

**Estructura**

- pages: donde estarán los elementos claves de nuestra aplicacion
- index: expondrá el sitio
- _app: archivos de configuracion
- api: en el caso de trabajar con una api
- public: donde estarán los archivos públicos imagenes o archivos claves para el proyecto
- styles: donde colocaremos los estilos de la aplicacion y los demás archivos de configuración

- Paso 4: ejecutamos el comando `npm run dev` y en la consola nos indica en que url podemos ver el proyecto por lo general es `http://localhost:3000`

## Paso 4: ESLint, Prettier y JSConfig con Next.js -> No lo recomiendo pero no esta demas saberlo 

> Debemos crear la carpeta src en la raíz del proyecto y mover a ésta las carpetas public, styles y pages. De esta forma tendremos acceso más fácil a los recursos, usando el path alias que agregamos en el archivo jsconfig.json. 


- Paso 1: Podemos crear nuestro directorio src y anexar ahi page, public, styles
- Paso 2: Creamos en raiz un config -> `jscongig.json` -> 
```
{
    "compilerOptions": {
        "baseUrl": "src",
        "paths": {
            "@pages": ["pages/"],
        }
    }
}

```
- Paso 3: .eslintignore Creamos este archivo para decirle que directorio no debe exportar  esto desde raíz. 
```
node_modules

```

- Paso 4: Cambiamos el nombre al archivo -> `.eslintrc.json` a `.eslintrc.js`
  - Configuraciones básicas, no hay una regla especifica no hay un standar unico 
  - Para crear standare de programción
```
module.exports = {
  root: true,
  env: {
      browser: true,//Me permite trabajar con el browser
      amd: true,//manejor de protocolos internos de js
      node: true,//
      es6: true,//para que activo los entornos de trabajo
  },
  extends: [//Me permite usar pluging o recomendaciones 
      'eslint:recommended',
      'plugin:jsx-a11y/recommended',// plugin para accesibildad
      'plugin:prettier/recommended',//configuración base para respetar los ;
      'next',//Configuraciones basicas
      'next/core-web-vitals',//Configuraciones basicas
  ],
  rules: {//Reglas 
      'semi': ['error', 'always'],//implementamos que se use ; 
  },
}
```

- Paso 5: creamos otro archivo de configuración mas standares de programación `prettier.config.js`

```
module.exports = {
    semi: true,//Obliga a usar cierre ;
    singleQuote: true,//obliga usar comilla doble para caracter
    printWidth: 200,//Maximo de caracter
    tabWidth: 2,//Tab a dos
    useTabs: false,
    trailingComma: 'es5',//Standar de eS5
    bracketSpacing: true,//
}
```

- Paso 6: Creamos el archivo `next.config.js`
```
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  env: {//Variables de entorno
    customKey: 'customValue',
  },
  basePath: '/dist',//Podemos definir elementos donde estara nuestro proyecto 
  compress: true,//Forma de presentar o compromir nuestro proyectp 
  async redirects() {//Forma de redireccionar 
    return [//Generas tu lista segun el caso la logica de tu app
      {
        source: '/hola',
        destination: 'https://gndx.dev',
        permanent: true,
      }
    ]
  }
}

module.exports = nextConfig

```

- Paso 7: Instalamos los elementos confifurados -> `npm install prettier eslint-plugin-prettier eslint-plugin-jsx-a11y eslint-config-prettier eslint-config-next`


## Clase 7: Alias y comunicación entre archivos

> En el archivo jsconfig.json podemos configurar elementos o reglas para este caso podemos anexar alias 

```
{
    "compilerOptions": {
      "baseUrl": "src",
      "paths": {
        "@icons/*": ["assets/icons/*"],
        "@logos/*": ["assets/logos/*"],
        "@context/*": ["context/*"],
        "@components/*": ["components/*"],
        "@styles/*": ["styles/*"],
        "@containers/*": ["containers/*"],
      }
    }
  }

```

## Clase 8: Sass

Instalamos sas `npm i sass` 

podemos usar las clases de esta manera 

```
className={`${styles["more-clickable-area"]} ${styles["navbar-email"]} ${styles.pointer}`}
```

## Clase 9: Sass

> Importante que en Next no podemos usar la etiqueta <img> debemos importar nuestras imaganes usando next/image

- Paso 1: Debemos importar la librería `import Image from 'next/image'`
- Paso 2: lo implementamos: 
```
<Image className="" width={50} height={50} src="/#" />
```


## Clase 13: next/link: enlaces en Next.js

> Es importante recordar que next tiene tambien su propio generador de enlaces este es llamado link. 

- Paso 1: Debemos importar la libreria en nuestro archivo donde lo deseamos usar: `import Link from 'next/link'`
- Paso 2: luego de importar lo podemos implementar de la siguiente forma. 
```
<link href="/#">
Titulo
</link>
```   

## Clase 14: Archivo de configuración y Google Analytics con Next.js 
> Recuerda que Next permite crear de manera automatica en el directorio page, transforma archivos .js ya con su ruta, pero si queremos que no haga esta transformación solo debemos colocar guion bajo para que no genere uan ruta. Ejemplo 

> Queremos transformar un archivo tipo documents. 

```
_document.js //llamandolo asi podemos generar un archivo 

import Document, { Html, Head, Main, NextScript } from 'next/document';

class MyDocument extends Document {
  render() {
    return (
      <Html lang="en">
        <Head>
          <title>React Shop</title>
          <script async src="https://www.googletagmanager.com/gtag/js?id=G-ZN80WG7H93"></script>
          <script
            dangerouslySetInnerHTML={{
              __html: `window.dataLayer = window.dataLayer || [];
            function gtag(){dataLayer.push(arguments);}
            gtag('js', new Date());
            gtag('config', 'G-ZN80WG7H93');`,
            }}
          />
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}

export default MyDocument;
```

**Ventajas**
- Permite que no pueda reconocer el CEO en la web
- Podemos generar meta datos
- Podemos generar o especificar detalle de nuestro detalle 
- Podemos usar NextScript para cargar nuestros elementos. 

## Clase 16:  Preparando la app para el deploy a producción
const withPWA = require('next-pwa');
const runtimeCaching = require('next-pwa/cache');

module.exports = withPWA({
  pwa: {
    dest: 'public',
    register: true,
    mode: 'production',
    disable: false,
    runtimeCaching,
    buildExcludes: [/middleware-manifest\.json$/],
  },
  reactStrictMode: true,
  images: {
    domains: ['placeimg.com'],
  },
});


-----------------------------------------------------------------------------------------------------
# Notas Curso Profesional de Next.js 
> Notas: 
- Documentación NEXT -> https://nextjs.org/docs/api-reference/create-next-app 

## Comandos para crear reglas de desarrollos 
- https://platzi.com/clases/2707-profesional-nextjs/46232-configuracion-de-eslint-y-prettier/ -> Clase 3 
```
npm i eslint-config-prettier eslint-plugin-jsx-a11y eslint-plugin-prettier prettier -D 
``` 
- "lint:fix": "eslint src/ --fix" -> Forma de arreglar usando script en package.json -> npm run lint

## Notas Conceptuales 

<!-- 
¿Que es ESLint?
ESLint es una utilidad de linting de JavaScript de código abierto creada originalmente por Nicholas C. Zakas en junio de 2013.
JavaScript, al ser un lenguaje dinámico y poco tipificado, es especialmente propenso a errores del desarrollador. Sin el beneficio de un proceso de compilación, el código JavaScript normalmente se ejecuta para encontrar errores de sintaxis u otros. Las herramientas de Linting como ESLint permiten a los desarrolladores descubrir problemas con su código JavaScript sin ejecutarlo.
 -->


<!-- 
¿Que es Prettier?
Prettier es un formateador automático de código.Al trabajar en un proyecto de código que incluya a más de una persona estas discusiones sobre como debería escribirse o no el código (guía de estilo) pueden mermar la productividad del equipo enfrascándose en nimiedades que pueden tornarse bastante molestas, por ejemplo, al revisar un pull-request. Las diferencias de estilo se mostrarán como cambios que en efecto no son parte del real desarrollo que se intenta lograr.
-->

## Notas PAra CSS usando potcss y tailwind - Instalar iconos y UI
- https://tailwindcss.com/docs/upgrade-guide#configure-content-sources
- npm i tailwindcss postcss autoprefixer -> Instala los paquetes 
- npx tailwindcss init -p -> Genera dos archivos para nuestra configuracion 
- Luego vamos al archivos raiz _app.js para agregar el importo de tailwind  ->  import '../styles/tailwind.css'
- npm i @heroicons/react @headlessui/react

## Nota para crear Alias ME SIGUE SIN FUNCIONAR 
- Generar nombre dela archivo jsconfig.json
```
{
  "compilerOptions": {
    "baseUrl": "src",
    "paths": {
      "@styles/*": ["styles/*"]
    }
  }
}
```


## Usando Cokies y Axios 
> Axios es un cliente HTTP basado en promesas para Node.js y el navegador.
- Podemos instalar los siguientes paquetes para poder usar cookies y bueno sabes que axios nos permite realizar llamados asyncornos
- `npm i js-cookie axios` 
```
import Cookie from 'js-cookie';
import axios from 'axios';

```
- Recuerda que puedes crear encanezados en axios 
- `axios.defaults.headers.Authorization = ` Bearer ${access_token.access_token}`;`


## Metodo MAP()
-  `{products?.map((lista) => ()}`  el simbolo de interrogación me permite validar si tiene valor 

## Tengo un paginador 
- practica\react-shop-admin\pages\dashboard\index.jsx
- practica\react-shop-admin\components\Paginate.js

## Crear Graficas 

- Paso 1: Instalamos pquetes: `npm i chart.js react-chartjs-2`
- Paso 2: Creamos nuestro componente tipo chart de barra -> practica\react-shop-admin\common\Chart.js
- Paso 3: Importamos donde lo necesitamos recordando que ese componenet recibe un arreglo con los datos ->practica\react-shop-admin\pages\dashboard\index.jsx
- Docs->https://www.chartjs.org/docs/latest/configuration/legend.html

## Explicacion del metodo arr.reduce()

```
Primero recordemos como funciona el reducer, este es un método de los arreglos que recibe un acomulador y un item como variable iteradora.

const countOccurrences = (array, value) => array.reduce((a,v) => (v === value? a : a), 0);

const countOccurrences = (arr) => arr.reduce((prev, curr) => ((prev[curr] = ++prev[curr] || 1), prev), {});

const reducer = (prev, curr) => {
    //prev es un acumulador y curr es el elemento actual del array que se recibe como parámetro,
    //es decir, un nombre de una categoría. 
    //La función .reduce() recorre todo el array, curr adquiere el valor de cada posición del array
    //prev[curr] es equivalente a tener obj[elemento]
    //Imaginemos el siguiente caso: 
    //prev = {shoes:1, others:3, clothes: 3}
    //Al hacer prev[curr] donde curr=shoes estámos llamando al valor del objeto prev cuya clave es shoes,
    //para este caso sería el valor de 1
 
    prev[curr] = ++prev[curr] || 1;
    //En la línea anterior accedemos al valor del objeto prev cuya clave es curr, recordemos que curr es 
    //un nombre de categoría que cambia con cada iteración. Si esa clave-valor no existe, como tiene un ||
    //entonces crea la clave-valor y le asigna el valor de 1, el primer conteo.
    //Si existe, entonces accede a ese valor y lo incrementa en 1, hace otro conteo*/

    return prev; //En cada iteración retornamos el objeto prev

    //Ejemplo:
   
    //Primera iteración: prev = {}, curr = "Shoes"
    //prev[curr] no existe, es decir no existe prev = {"Shoes":algunNumero}, entonces se le asigna 1,
    //quedando: prev = {"Shoes":1}
    
    //Segunda iteración: se retornó prev que es nuestro valor acumulado, actualmente prev = {"Shoes":1}
    //Ahora curr = "Others", entonces tendríamos: 
    //prev = {"Shoes":1,"Others":1}

    //Tercera iteración: prev = {"Shores:1","Others":1} curr = "Shoes"
    //Accedemos a prev[curr], esta vez sí existe, como existe incrementamos su valor actual, quedando ahora en 2
    //prev = {"Shoes":2,"Others":1}

    
  };

  /*Creamos la función para contar, en la función .reduce() pasamos nuestra función reducer y el valor inicial
    de prev que es un objeto vacío.
  */
  const countCategories = (array) => categoryNames.reduce(reducer, {});
```

## Como generar Rutas dinamicas 

- Paso 1: crear un directorio para este ejemplo uno para editar (edit)
- Paso 2: Paso dentro de este directorio debes generar el archivo dinamico de esta manera [id].js para que este pueda generar la ruta dinamica

## Manera de deployar olvidando los errores de npm run build 

```
Debes crear un archivo en la raiz con nombre -> next.config.js 


module.exports = {
  reactStrictMode: true,
  eslint: {
    ignoreDuringBuilds: true,
  },
};
```


## Pasos para usar Versel y desplegar 
- Paso 1: Ejecutamos este comando para generar la estructura ->  `npm run build`
- Paso 2: Podemos ejecutar este comando pras reparar algunos errores ->`npm run lint:fix`
- Paso 3: Podemos crear un repositorio en github para montarlo en vercel 
- Paso 4: Si no tienes cuenta vercel creada debes crear una. `https://vercel.com/`
- Paso 5: Entramos a vercel ubicamo la parte para vincularlo con github colocando el nombre del 
- Paso 6: Debemos configurar las variables de entornos 
![Variables Entorno](../info/VariablesEntorno.png)

  repositorio 
- Paso 7: Clic en Deploy [Ver la clase](https://platzi.com/clases/2707-profesional-nextjs/46255-haciendo-el-deploy-de-nuestra-aplicacion-en-vercel/)
 