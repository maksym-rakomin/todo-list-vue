<template>
  <form @submit.prevent="onSubmit">
      <input type="text" name="#" v-model="title">
      <button type="submit">
          Добавить задачу
      </button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            console.log('sudmit', this.title)

            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    },
}
</script>

<style>
    form {
        display: flex;
        justify-content: center;
    }
    input {
        flex: 1 1 60%;
        font-size: 1.5rem;
        padding: 0.5rem;
    }
</style>