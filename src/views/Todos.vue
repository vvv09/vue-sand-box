<template>
    <div>
        <router-link to="/">home</router-link>
        <hr>
        <AddTodo @add-todo="addTodo"/>
        <hr>
        <div v-if="loading">
            <Loader/>
            <p>тащим...</p>
        </div>
        <TodoList
                v-else-if="todos.length"
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
    import Loader from '@/components/Loader'

    export default {
        name: 'app',
        data() {
            return {
                todos: [],
                loading: true
            }
        },
        mounted() { // чтобы запрос выпонялся когда комонент подготовил шаблон и поместил его в дерево
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(response => response.json())
                .then(json => {
                    setTimeout(() => {
                        this.todos = json
                        this.loading = false
                    }, 5000) // искусственная задержка чтобы видеть лоадер
                })
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
            AddTodo,
            Loader
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
