<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notes
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                    <div  class="md:grid md:grid-cols-3 md:gap-6">
                       <div  class="md:col-span-1">
                        <div class="px-4 sm:px-0">
                        <h3 class="text-lg text-gray-900">Listado de notas</h3>
                        <p class="text-sm text-gray-600">
                        Toma el registro correcto y ejecuta calquier funcion (ver,editar,eliminar)</p>
                        </div>
                       </div>
                    </div>
                
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout'
    import Welcome from '@/Jetstream/Welcome'

    export default {
        components: {
            AppLayout,
            Welcome,
        },
    }
</script>
