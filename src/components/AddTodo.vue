<template>
  <form @submit="addTodo">
    <input type="text" placeholder="new work" v-model="title" >
    <input type="submit" value="Them" class="add-btn">
  </form>
</template>

<script>
import {ref} from 'vue'
//import {v4 as uuidv4} from 'uuid'
export default {
   name: 'AddTodo',
   setup(props,context) {
    const title = ref('')

    const addTodo = event => {
      event.preventDefault();

      const newItem = {
        //id: uuidv4,
        title: title.value,
        completed: false
      }
      context.emit('add-todo',newItem)

      title.value = ''
    }
    
    return { title,addTodo}
   }
}
</script>

<style>
form {
    display: flex;
}

input[type='text'] {
    flex: 10;
    padding: 5px;
}

input[type='submit'] {
    flex: 2;
}
</style>