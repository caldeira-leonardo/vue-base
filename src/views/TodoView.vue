<script setup>
import CustomTodoComponent from '@/components/CustomTodoComponent.vue';
import { ref, onMounted, watch } from "vue";

const todos = ref([]);
const text = ref("");

//armazenar os dados no local storage
watch(todos, (newTodoValue) => {
  localStorage.setItem("todos", JSON.stringify(newTodoValue));
}, { deep: true });

//recuperar do local storage
onMounted(() => {
  todos.value = JSON.parse(localStorage.getItem('todos') || []);
});

//editar um to-do
function editTodo(id, newTodo) {
  todos.value = todos.value.map((todo) =>
    todo.id === id ? { ...todo, text: newTodo } : todo
  );
}

//deletar um to-do
function deleteTodo(todo) {
  todos.value = todos.value.filter((x) => x !== todo);
}

</script>

<template>
  <main class="flex flex-col items-center justify-center font-sans gap-12">
    <section>
    <InputGroup>
      <InputText class="" type="text" v-model="value" placeholder="Adicionar to-do..." />
      <TheButton
        class=""
        icon="pi pi-plus"
        @click="aaa"
        :disabled="todos === 'a'"
      />
    </InputGroup>
    </section>
    <section>
      <CustomTodoComponent needtodo=""/>
    </section>
  </main>
</template>
