<template>
    <div>
        <label v-bind:class="{'is-done':todo.completed}">
            <input type="checkbox"
                   v-bind:checked="todo.completed"
                   v-on:change="changeTodo"/>
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)">X</button>
        </label>
    </div>
</template>

<script>

    export default {
        name: "TodoItem",
        props: ["todo"],
        methods: {
            changeTodo(){
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    div {
        border: 1px solid #ccc;
        text-align: left;
        padding: 15px;
        border-radius: 2px;
        margin: 10px;
        box-shadow: 0 0 2px #ccc;
    }
    .is-done {
        text-decoration: line-through;
    }

</style>