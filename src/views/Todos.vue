<template>
    <div>
        <router-link to="/">home</router-link>
        <hr>
        <AddTodo @add-todo="addTodo"/>
        <hr>
        <TodoList
                v-if="todos.length"
                v-bind:todoss="todos"
                @remove-todoi="removeTodo"
        />
        <!--@remove-todoi тоже что и v-on:remove-todoi-->
        <p v-else>No todos!</p>
    </div>
</template>

<script>
    import TodoList from '@/components/TodoList'
    import AddTodo from '@/components/AddTodo'

    export default {
        name: 'app',
        data() {
            return {
                todos: []
            }
        },
        mounted() { // чтобы запрос выпонялся когда комонент подготовил шаблон и поместил его в дерево
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(response => response.json())
                .then(json => this.todos = json)
        },
        methods: {
            removeTodo(id) {
                this.todos = this.todos.filter(t => t.id !== id)
            },

            addTodo(todo) {
                this.todos.push(todo);
            }
        },
        components: {
            TodoList,
            AddTodo
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    h4, h5 {
        color: gray;
        margin: 0px 0px;

    }
</style>
