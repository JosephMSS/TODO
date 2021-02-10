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
   En las vistas vue mepleamos codigoe javascript para acceder a las propiedades del objeto.

### Edicion de los datos

Para poder enlazar los datos de un objeto a un formulario debemos hacer ingresar los siguientes valores en el script expor default, dentro de form vamos a asignar los espacion que necesitamos y asignamos los datos del objeto al cual pertenece.

```
data() {
       return {
           form: {
           excerpt: this.note.excerpt,
           content: this.note.content
       }
       }
   }
```

ademas debemmos enlazar los input a estos datos con el atributo v-model

```
<textarea v-model="form.content"
rows="8"
class="form-input w-full rounded-md shadow-sm"></textarea>
```

## Update

> Podemos agregar en el foulario el metodo `submit.prevent='submit'`, prevent evita que se recargue el formulario y el valor submit hace referencia a un metodo configurado en los scripts

```
methods:{
        submit(){
            this.inertia.put(this.route('notes.update',this.note.id),this.form)
        }
```

En donde por medio de `inertia.put`(este puede ser: post, delete) enviamos la ruta,id y con el objeto `form` enviamos la informacion que se encuentra en el formulario.

## [Formuario de create](resources\js\Pages\Notes\Create.vue)

En este caso los cambios especificos que haces es eliminar la popiedad del objeto y ademas inicializar los datos del form vacio, para que a medida de que se crea el objeto este se vaya llenando con los espacios enlazados, y al momento de ejecutar la accion submit enviamos el formulario que se encuantra enlazado a las cajas. `Recordar que el formulario no lleva el atributo action, se cambia por el atributo submit.prevent`

## [Eliminar](resources\js\Pages\Notes\Edit.vue)

Para eliminar un formulario debemos hace la configuacion del evento destroy

### Flash Message

Debemos crar un canal de comunicacion entre laravel y vue para podern enviar este tipo de mensajes.

1. Ingreasamos a la carpeta archivo de [Providers](app\Providers\AppServiceProvider.php).
   use Illuminate\Support\Facades\Session;
    - Importamos el componente de Inertia y Session[(Componente de Laravel que nos premita trabajar con las sesiones)]()
    - Configuramos el metodo `boot`, en donde empleamos estas clases y cnfiguramos la variable de sesion que necesitamos.
    - Uso de variable flash
    ```
   <div v-if="$page.props.flash.status" class="bg-blue-500   text-white text-sm font-bold p-4">
      <p>{{$page.props.flash.status}}</p>
   </div>
    ```
