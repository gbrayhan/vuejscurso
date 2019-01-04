# Curso de Vuejs - Platzi

Hola mundo en Vuejs
  
 ```js  
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

 ```js  
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
  
 ```js  
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