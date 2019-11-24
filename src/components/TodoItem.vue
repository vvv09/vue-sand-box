<template>
    <li>
        <span>
            <input type="checkbox">
            <strong>{{todoitem.id}}</strong>
            {{todoitem.title}}
        </span>
        <button>&times;</button>
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