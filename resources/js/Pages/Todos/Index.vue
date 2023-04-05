<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, useForm } from "@inertiajs/vue3";

defineProps(['todos']);
 
const form = useForm({
    content: '',
});

</script>

<template>
  <Head title="Todos" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Todo List
      </h2>
    </template>

    <div class="py-12">
      <div class="w-300 mx-6 sm:px-6 lg:px-8 bg-slate-50" >
        <form @submit.prevent="form.post(route('todos.store'), { onSuccess: () => form.reset() })">
          <div class="mb-6">
            <label
              for="todo"
              class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
              >Todo</label
            >
            <input
              type="text"
              id="todo"
              class="bg-gray-50 border w-96 border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
              placeholder="your Task" v-model="form.content"
              required
            />
            
            <input
            type="submit" value="Ajouter" @click.prevent="submit"
            class="text-white  bg-blue-700 mx-4 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
            />
            </div>
        </form>
      </div>
      <div class="mt-6 bg-white shadow-sm rounded-lg divide-y">
                <div  v-for="todo in todos"
                    :key="todo.id"
                    :todo="todo">
                    

                </div>
                   
              
            </div>
    </div>
  </AuthenticatedLayout>
</template>
