<template>
    <div>


        <ul>
            <li v-for="todo in allTodos" v-bind:key="todo.id">
                <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
            </li>
        </ul>
    </div>
</template>

<script>
    import { mapGetters, mapActions} from 'vuex';

    import TodoItem from './TodoItem';

    export default {
        name: "TodoList",
        methods: {...mapActions(['fetchTodos'])},
        computed: mapGetters(['allTodos']),
        created() {
            this.fetchTodos();
        },
        components: {
            TodoItem
        }
    }
</script>

<style>
    ul {
        list-style: none;
        margin: 20px 0;
        padding: 0;
    }
    li {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>