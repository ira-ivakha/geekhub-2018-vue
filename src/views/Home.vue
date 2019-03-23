<template>
  <div id="app">
    <h1>Todo list</h1>
    <AddTodo v-on:add-todo="addTodo"/>
    <TodoList v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
    import AddTodo from '../components/AddTodo';
    import TodoList from '../components/TodoList';
    import axios from 'axios';

    export default {
        name: 'app',
        components: {
            TodoList,
            AddTodo
        },
        data() {
            return {
                todos: []
            }
        },
        methods: {
            deleteTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id);
            },
            addTodo(newTodo) {
                this.todos = [...this.todos, newTodo];
            }
        },
        created(){
            axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
                .then( res => this.todos = res.data)
                .catch(err => {console.log(err); return false;})
        }
    }
</script>

<style>

</style>
