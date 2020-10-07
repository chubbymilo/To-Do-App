<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
   <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import axios from 'axios'

import Vue from 'vue'
import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue.use(BootstrapVue)
Vue.use(BootstrapVueIcons)

export default {
  name: 'App',
  components: {
    Todos,
    AddTodo
  },
  data(){
    return{
      todos:[
        /*
        {
          id:1,
          title:"To do One",
          completed:false
        },
        {
          id:2,
          title:"Todo two",
          completed:false
        },
        {
          id:3,
          title:"Todo three",
          completed:false
        }
        */
      ]
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://localhost:44325/api/TodoItems/${id}`)
      //used () to replace res to avoid error. 
      .then(() => this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));
    },
    addTodo(newTodo){
      const {title, completed} = newTodo;

      axios.post('https://localhost:44325/api/TodoItems',{
        title,
        completed
      }).then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err))
    }
    },
   created(){
      axios.get('https://localhost:44325/api/TodoItems')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>

</style>
