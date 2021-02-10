# Instalacion

1. > `laravel new [Nombre del proyecto] --jet`
2. > Seleccionamos la opcion de inertia
3. > Instalamos los modulos de node
   > `npm instal & npm run dev`

## Creacion de controlador resource, factory y migracion

`php artisan make:model Note -rfm`

## Configuracion inicial

Los componentes de las vistas se encuentran el la carpeta `resources\js\Pages\`, estos son los archivos que se renderisan dentro del archivo `resources\js\app.js` en dnde debemos colocar nuestros archivos para cumplir dicha configuracion.

### [Controlador de pagina](app\Http\Controllers\PageController.php)

En este proyecto nuestra pagina privada va a ser la vista dashboard.
Vamos a invocar esta vista por medio del controlador por medio del metodo `dashboard`.

> Para poder retornar esta vista debemos emplearla clase de Inertia para poder renderizar el componente que se encuentra en `resources\js\Pages\` .

> Por ultimo configuramos la ruta de tipo recurso para el controlador de notas.

## Pesonalizacion

Recordar que cada ves que hagamos un cambio en los componentes debemos renderizarlos de nuevo para que se ejecuten los cambios, esto con `npm run watch`

> La configuracion delos botones de las rutas la podemos ejecutar por medio del componente `resources\js\Layouts\AppLayout.vue`, asi personalizamos el componente

## [Uso de colecciones en las vistas](resources\js\Pages\Notes\Index.vue)

Para poder hacer uso de las colecciones debemos ir al script e indicarle en el export default
que va a tener la propiedad props y dentro va a contener el nombre de la variable y el tipo:

```
props{
notes: Array,
}
```

Esta variable es la que estamos mandando desde el controlador

### Recorrido de collecciones

```
<table>
         <tr v-for="(note, i) in notes" :key="i">//De esta manera recorremos el array
            <td class="border px-4 py-2">
                  {{ note.excerpt }}
            </td>
            <td class="px-4 py-2">
                <inertia-link :href="route('notes.show',note.id)">
                                            Ver
                 </inertia-link>
            </td>
         </tr>
</table>

```

### Division de un componente VUE

Este se puede dividir en tres secciones:

1. Plantilla
2. Scripts
3. Estilos
 En las vistas vue mepleamos codigo javascript para acceder a las propiedades del objeto. 
