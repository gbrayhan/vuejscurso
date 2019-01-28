# Curso de Vuejs - Platzi  
  
Hola mundo en Vuejs  
  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue.js</title>
</head>
<body>
    <div id="app">
        Hola {{ nombre }}
        <a v-bind:href="url" target="_blank">{{ pagina }}</a>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                nombre: 'David',
                url: 'https://google.com',
                pagina: 'Google'
            }
        })
    </script>
</body>
```
  
Las variables de **vuejs** no se pueden utilizar en los atributos de las etiquetas.   
En la consola se puede acceder a las variables Vuejs de la siguiente manera:  
  
[Consola del navegador]  
  
`app.nombre="Alejandro"`  
`this.app.nombre="Alex"`  
    
Manejo de condiciones con Vuejs.  
  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue.js</title>
</head>
<body>
    <div id="app">
        <template v-if="mostrar">
            <h1>Titulo</h1>
            <h2>Subtitulo</h2>
            <p> Hola {{ nombre }} </p>
            <a v-bind:href="url" target="_blank">{{ pagina }}</a>
        </template>  
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                nombre: 'David',
                url: 'https://google.com',
                pagina: 'Google',
                mostrar: true
            }
        })
    </script>
</body>
```

  
Es recomendable utilizar la etiqueta template que no es visible en el DOM y ahi agregarle la condicional de **v-if**.  
Otra herramienta de vuejs es **v-show** que el navegador entiende de una mejor manera para el navegador, la desventaja es que no se puede utilizar los **templates** de vuejs.  
  
  
Los datos en vuejs pueden filtrase a partir de metodos previamente definidos, como se muestra a continuacion:  

```html  
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue.js</title>
</head>
<body>
    <div id="app">
        <template v-if="mostrar">
            <h1>{{ titulo | uppercase }}</h1>
            <h2>{{ subtitulo | uppercase | lowercase }}</h2>
              <p> Hola {{ nombre }} </p>
            <a v-bind:href="url" target="_blank">{{ pagina }}</a>
        </template>  
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                nombre: 'David',
                url: 'https://google.com',
                pagina: 'Google',
                mostrar: true,
                titulo: "Curso de Vuejs" ,
                subtitulo: "Introduccion a Vuejs"
            },
            filters: {
                uppercase: function(str) {
                    return str.toUpperCase()
                },
                lowercase: function(str) {
                    return str.toLowerCase()
                }
            }
        })
    </script>
</body>
```
  
Cabe señalar que se pueden aplilar los metodos que se ejecutan sobre una variable, y estos son con el orden de izquierda a derecha, en el codigo anterior se ejemplifica lo antes mencionado de la siguiente manera.  
`{{ subtitulo | uppercase | lowercase }} `  
  
  
### Eventos en vuejs  
  
Se pueden crear metodos que se mandan a llamar a partir de eventos del navegador, a continuacion de muestra como se implementan un sumador y un decrementador que se ejecutan luego de dar click. El atributo que se agrega a la etiqueta es **v-on:click="sumar"** y el codigo completo es el siguiente.  
  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue.js</title>
</head>
<body>
    <header>Aplicacion de Vuejs</header>
    <div id="app">
        <button v-on:click="sumar">Sumar</button>
        <button v-on:click="restar">Restar</button>
        <h2>Resultado</h2>
        <h3>{{ contador }}</h3>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                contador: 0
            },
            methods: {
                sumar: function() {
                    this.contador ++
                },
                restar: function() {
                    this.contador --
                } 
            }
        })
    </script>
</body>
```
  
Si se utiliza un **arrow function**, no se cambia la variable que instanciamos en vuejs. Las arros function en vue son un antipatron ya que hace referencia a lo que esta fuera de "app".   
  
### Manejo de formularios  

Vuejs permite realizar distintas acciones sobre los formularios, incluso interrumpir la ejecucion de envio del formulario con el trubuto **v-on:submit.prevent="metodoEnviar"** en la etiqueta de **form** y los elementos input pueden trabajar dinamicamente con vuejs utilizando los **v-model**. A continuacion se muestra el codigo con el uso de vuejs en formularios.  
  
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Vue.js</title>
</head>

<body>
    <div id="app">
        <input type="text" name="nombre" placeholder="Ingresa tu nombre" v-model="nombre">
        <p>Tu nombre en mayusculas es: {{ nombre | uppercase}} </p>

        <form v-on:submit.prevent="metodoEnviar" action="get">
            <h2>Cuales son tus cursos favoritos</h2>
            <input type="checkbox" v-model="cursos" id="vue" value="vue">
            <!-- sincronizar con el id -->
            <label for="vue">Vue js</label>

            <input type="checkbox" v-model="cursos" id="php" value="php">
            <label for="php">Curso de PHP</label>
            <input type="checkbox" v-model="cursos" id="php" value="react">
            <label for="react">Curso de React</label>
            
            <br>
            <button type="submit">Enviar</button>
        </form>
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
        var app = new Vue({
            el: '#app',
            data: {
                nombre: '',
                cursos: []
            },
            filters: {
                uppercase: function (str) {
                    return str.toUpperCase()
                },
                lowercase: function (str) {
                    return str.toLowerCase()
                }
            },
            methods: {
                metodoEnviar: function () {
                    console.log(this.cursos)
                }
            }

        })
    </script>
</body>
```



