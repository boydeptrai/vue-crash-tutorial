<template>
  <TodoListItem
    v-for="todo in todos"
    :key="todo.id"
    :todoProps="todo"
    @item-completed="markComplete"
    @delete-item="deleteTodo"
  />
</template>

<script>
import { ref } from 'vue';
import TodoListItem from './TodoListItem.vue';
export default {
  name: 'TodoItem',
  components: {
    TodoListItem,
  },
  setup() {
    const todos = ref([
      {
        id: '1',
        title: 'Viec 1',
        completed: false,
      },
      {
        id: '2',
        title: 'Viec 2',
        completed: false,
      },
      {
        id: '3',
        title: 'Viec 3',
        completed: false,
      },
    ]);
    
    const markComplete = id =>{
     todos.value =todos.value.map((todo) =>{
      if (todo.id === id) todo.completed = !todo.completed
      return todo
     })
    }

    const deleteTodo = id =>{
      todos.value = todos.value.filter(todo =>todo.id !== id)
    }
    return { todos,markComplete,deleteTodo };
  },
};
</script>

<style></style>
