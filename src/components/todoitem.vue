<template>
    <li>
        <div class="list-item" v-bind:class="{done: todo.completed}">
            <input type="checkbox" name="#"
                v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            <p>{{todo.title | uppercase}}</p>
        </div>
        <button class="btn-rem"
            v-on:click="$emit('remove-todo', todo.id)">
            &times;
        </button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value) {
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: 0.5rem 2rem;
        margin-bottom: 1rem;
    }

    .btn-rem {
        background-color: #2472e7;
        color: black;
        width: 1.5rem;
        height: 1.5rem;
        border-radius: 50%;
        border: none;
        font-weight: bold;
        cursor: pointer;
        align-self: center;
        transition: all .3s ease;
    }
    .btn-rem:hover {
        background-color: #e93333;
    }
    input {
        margin-right: 1rem;
        flex-basis: 5%;
    }
    strong {
        flex-basis: 5%;
        margin-right: 1rem;
    }
    p {
        flex-basis: 90%;
        margin-right: 1rem;
        text-align: left;
    }
    .list-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-basis: 100%;
    }
    .done {
        text-decoration: line-through;
    }
</style>