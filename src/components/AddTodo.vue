<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo">
            <input type="submit" value="Add Todo" class="button">
        </form>
    </div>
</template>

<script>
    import uuid from 'uuid';
    export default {
        name: "AddTodo",
        data(){
            return {
                title: ''
            }
        },
        methods: {
            addTodo(e){

                e.preventDefault();
                if (this.title!=='') {
                    const newTodo = {
                        id: uuid.v4(),
                        title: this.title,
                        completed: false
                    };

                    this.$emit('add-todo', newTodo);
                    this.title = '';

                }

            }
        }
    }
</script>