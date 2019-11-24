<template>
    <div>
        <ul>
            <TodoItem
                v-for="(todo, i) of todoss"
                v-bind:todoitem="todo"
                v-bind:indexx="i"
                v-on:remove-todoi="removeTodo" />
                <!--по получении от чайлда события с именем "remove-todoi"
                                выполнить функцию "removeTodo"-->
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem'

    export default {
        props: ['todoss'],
        components: {
            TodoItem
        },
        methods: {
            removeTodo(id) {
                this.$emit('remove-todoi', id); //пересылаем родителю
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>