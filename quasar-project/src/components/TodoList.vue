<template>
    <div>
      <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove="handleDelete(todo.id)" @update="handleEdit" @completed="handleCompleted"/>
    </div>
</template>
<script>
import { defineComponent } from 'vue'
import TodoItem from "components/TodoItem.vue";

export default defineComponent({
    name: "TodoList",
  components: {TodoItem},

    props: {
        todos: {
            type: Array,
            required: true,
        }
    },
    emits:['remove', 'update'],
    methods: {
      handleDelete(id) {
        this.$emit('remove', id)
      },
      handleEdit(newTodo) {
        console.log(newTodo)
        this.$emit('update', newTodo)
      },
      handleCompleted(id){
        this.$emit('completed', id)
      }
    }
})
</script>
