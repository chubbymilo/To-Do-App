<template>
<div>
    <h1 class="text-center">My To-Do List</h1>
    <div  v-bind:key="todoItem.id" v-for="todoItem in todos">
        <b-list-group>
    <TodoItem v-bind:todoItem="todoItem" v-on:del-todo="$emit('del-todo',todoItem.id)"/>
        </b-list-group>
    </div>
</div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
    name:"todos",
    components:{
        TodoItem
    },
    //Passing data from APP.vue
    props:["todos"]   
}
</script>

<style scoped>

</style>