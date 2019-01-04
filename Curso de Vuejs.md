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
  
Manejo de condiciones con Vuejs
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
            
            Hola {{ nombre }}
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



