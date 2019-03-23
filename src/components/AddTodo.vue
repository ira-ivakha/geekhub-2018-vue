<template>
    <div>
        <form @submit="onSubmit">
            <input type="text" v-model="title" name="title" placeholder="Add Todo">
            <input type="submit" value="Add Todo" class="button">
        </form>
    </div>
</template>

<script>
    import uuid from 'uuid';
    import { mapActions } from 'vuex';
    export default {
        name: "AddTodo",
        data(){
            return {
                title: ''
            }
        },
        methods: {
            ...mapActions(['addTodo']),
            onSubmit(e){

                e.preventDefault();
                if (this.title!=='') {

                    this.addTodo(this.title);
                    this.title = '';

                }

            }
        }
    }
</script>
<style>
    input[type=text] {
        font-family: inherit;
    }
</style>