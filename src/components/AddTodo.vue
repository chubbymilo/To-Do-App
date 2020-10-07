<template>
<div>
    <b-form @submit="addTodo" class="text-center mb-3">
        <b-form-input type="text" v-model='title' name="title" placeholder = "Enter a new to-do task"/>
        <b-button type="submit" class="mt-2">Submit</b-button>
    </b-form>
</div>    
</template>

<script>
//import {v4 as uuid} from 'uuid';
export default {
    names: "AddTodo",
    data(){
        return {
            title: ''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();

            const newTodo = {
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
            this.title = '';
        }
    }
    
}
</script>

<style scoped>

</style>