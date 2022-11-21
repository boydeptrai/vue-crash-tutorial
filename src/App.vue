<template>
  <div id="app">
    <TheHeader />
    <TodoItem />
  </div>
</template>

<script>
import TheHeader from './components/TheHeader';
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    TodoItem
  },
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
