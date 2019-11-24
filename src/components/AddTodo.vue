<template>
    <!-- prevent упрощенный preventDefault
        чтобы избежать реакции браузера не сабмит формы -->
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="anyTitleName">
        <button type="submit">Create</button>
    </form>
</template>

<script>
    export default {
        data() {
          return {
              anyTitleName: ''
          }
        },
        methods: {
            onSubmit() {
                if (this.anyTitleName.trim()) {
                    const newTodo = {
                        id: Date.now(),
                        title: this.anyTitleName,
                        completed: false
                    }
                    this.$emit("add-todo", newTodo);
                    this.anyTitleName = '';
                }

            }
        }
    }
</script>

<style scoped>
    input {
        width: 400px;
    }
</style>