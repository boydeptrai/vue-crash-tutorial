<template>
  <p :class="['list-item',todoProps.completed ? 'is-completed' : '']">
    <input type="checkbox" :checked="todoProps.completed" @change="markItemCompleted">
    {{todoProps.title}}
    <button class="del-btn" @click="deleteItem">Delete</button>
  </p>
</template>

<script>
export default {
   name: 'TodoListItem',
   props: ['todoProps'],
   setup(props,context) {
    const markItemCompleted = () =>{
       context.emit('item-completed',props.todoProps.id)
    }

    const deleteItem = () => {
       context.emit('delete-item',props.todoProps.id)
    }
    return { markItemCompleted,deleteItem}
   }
}
</script>

<style>
.list-item {
    background-color: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}

.is-completed {
    text-decoration: line-through;
}

.del-btn {
    background-color: #ff0000;
    color: #fff;
    border: none;
    float: right;
    cursor: pointer;

}
</style>