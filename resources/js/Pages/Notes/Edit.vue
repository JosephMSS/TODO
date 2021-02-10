<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notes
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px-0">
                            <h3 class="text-lg text-gray-900">
                                Detalle de una nota
                            </h3>
                            <p class="text-sm text-gray-600">
                                {{ note.excerpt }}
                            </p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form>
                                <label
                                    class="block font-medium text-sm text-gray-700"
                                    >Resumen</label
                                >
                                <textarea
                                    v-model="note.excerpt"
                                    class="form-input w-full rounded-md shadow-sm"
                                ></textarea>
                                <label
                                    class="block font-medium text-sm text-gray-700"
                                    >Contenido</label
                                >
                                <textarea
                                    v-model="form.content"
                                    rows="8"
                                    class="form-input w-full rounded-md shadow-sm"
                                ></textarea>
                                <button
                                    class="rounded-md  bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4"
                                >
                                    Editar
                                </button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import Welcome from "@/Jetstream/Welcome";

export default {
    components: {
        AppLayout,
        Welcome
    },
    props: {
        note: Object
    },
    data() {
        return {
            form: {
            excerpt: this.note.excerpt,
            content: this.note.content
        }
        }
    }
};
</script>
