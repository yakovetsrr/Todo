<template>
    <div>
        <div v-for="todo in todos" :key="todo.id">
            {{ todo.name }}
        </div>
    </div>
</template>
<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: "TodoList",
    props: {
        todos: {
            type: Array,
            required: true,
        }
    }
})
</script>