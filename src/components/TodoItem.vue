<template>
<div v-bind:class="{'isCompleted':todoItem.completed}">

  <b-list-group-item class="text-center">
      <span class="align-middle"><input class="mr-3" type="checkbox" v-on:change="markComplete"/>{{todoItem.title}}</span>
      <b-button @click="$emit('del-todo',todoItem.id)" class="ml-3">Delete</b-button>
      </b-list-group-item> 
</div>    
</template>

<script>
export default {
    name:"TodoItem",
    //Passing data from Todos.vue
    props:["todoItem"],
    methods:{
        markComplete(){
            this.todoItem.completed = !this.todoItem.completed;
        }
    }
    
}
</script>

<style scoped>
.isCompleted{
    text-decoration: line-through;
}
</style>