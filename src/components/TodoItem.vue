<template>
  <TodoListItem v-for="todo in todos" :key="todo.id" :todoProps="todo" />
</template>

<script>
import { ref } from 'vue';
import TodoListItem from './TodoListItem.vue'
export default {
  name: 'TodoItem',
  components: {
    TodoListItem
  },
  setup() {
    const todos = ref([
        {
            id: "1",
            title: 'Viec 1',
            completed: true
        },
        {
            id: "2",
            title: 'Viec 2',
            completed: false
        },
        {
            id: "3",
            title: 'Viec 3',
            completed: false
        },
    ]);

    return { todos };
  },
};
</script>

<style></style>
