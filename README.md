# Instalacion
1. > `laravel new [Nombre del proyecto] --jet`
2. > Seleccionamos la opcion de inertia
3. >Instalamos los modulos de node
 `npm instal & npm run dev`
 ## Creacion de controlador resource, factory y migracion
  `php artisan make:model Note -rfm`
  ## Configuracion inicial
  Los componentes de las vistas se encuentran el la carpeta `resources\js\Pages\`, estos son los archivos que se renderisan dentro del archivo  `resources\js\app.js` en dnde debemos colocar nuestros archivos para cumplir dicha configuracion.
  ### [Controlador de pagina](app\Http\Controllers\PageController.php)
  En este proyecto nuestra pagina privada va a ser la  vista dashboard.
  Vamos a invocar esta vista por medio del controlador por medio del metodo `dashboard`.
  > Para poder retornar esta vista debemos emplearla clase  de  Inertia para poder renderizar el componente que se encuentra en `resources\js\Pages\` .
  
  > Por ultimo configuramos la ruta de  tipo recurso para el controlador de notas.