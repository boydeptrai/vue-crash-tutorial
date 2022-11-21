<template>
  <AddTodo @add-todo="addTodo" />
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
import AddTodo from './AddTodo.vue'
import {v4 as uuidv4} from 'uuid'
export default {
  name: 'TodoItem',
  components: {
    TodoListItem,
    AddTodo
  },
  setup() {
    const todos = ref([
      {
        id: uuidv4,
        title: 'Viec 1',
        completed: false,
      },
      {
        id: uuidv4,
        title: 'Viec 2',
        completed: false,
      },
      {
        id: uuidv4,
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

    const addTodo = newTodo =>{
      todos.value.push(newTodo)
    }
    return { todos,markComplete,deleteTodo,addTodo };
  },
};
</script>

<style></style>
