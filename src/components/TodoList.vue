<template>
    <div>
        <ul>
            <TodoItem
                v-for="todo of todoss"
                v-bind:todoitem="todo"
            />
        </ul>
    </div>
</template>

<script>
    import TodoItem from '@/components/TodoItem'

    export default {
        props: ['todoss'],
        components: {
            TodoItem
        }
    }
</script>