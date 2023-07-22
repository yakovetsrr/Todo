<template>
  <q-page>
    <TodoCreateForm @submit="createTodo" />
    <TodoList :todos="todos" @remove="deleteTodo" @update="handleEdit" @completed="handleCompleted"/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import TodoCreateForm from 'src/components/TodoCreateForm.vue';
import TodoList from 'src/components/TodoList.vue';

export default defineComponent({
  name: "IndexPage",
  components: { TodoCreateForm, TodoList },

  data() {
    return {
      todos: [],
    };
  },
  methods: {
    createTodo(name) {
      console.log('name', name);
      this.todos.push({
        id: Date.now(),
        name: name,
        completed: false,
      })
    },
    deleteTodo(id) {
      console.log('id', id);
      this.todos = this.todos.filter((todo) => todo.id !== id )
    },
    handleEdit(newTodo) {
      const index = this.findTodoIndexById(newTodo.id)
      this.todos[index] = newTodo;
    },
    handleCompleted(id){
      const index = this.findTodoIndexById(id)
      this.todos[index].completed = !this.todos[index].completed;
    },
    findTodoIndexById(id){
      return this.todos.findIndex((todo)=> todo.id===id)
    }
  },
})

</script>




