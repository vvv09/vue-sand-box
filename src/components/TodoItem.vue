<template>
    <li>
        <span v-bind:class="{done: todoitem.completed}">
            <input type="checkbox" v-on:change="todoitem.completed = !todoitem.completed">
            <strong>{{todoitem.id}}</strong>
            {{todoitem.title}}
        </span>
        <button class="deletebtn" v-on:click="$emit('remove-todoi', todoitem.id)">&times;</button>
        <!--  $emit('remove-todoi', todoitem.id) - сообщаем родительскому эл-ту
              о произошедшем событии и передаем этому эл-ту данные -->
    </li>
</template>

<script>
    export default {
        props: { //валидация входящих праметров
            todoitem: {
                type: Object,
                required: true
            }
        }
    }
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }

    .deletebtn {
        background: red;
        color: #fff;
        border-radius: 50%;
        border: none;
        font-weight: bold;
    }

    input {
        margin-right: 1rem;
    }

    .done{
        text-decoration: line-through;
    }
</style>