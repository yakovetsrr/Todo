<template>
  <q-page>
    <TodoCreateForm @submit="createTodo"/>
    <TodoList :todos="todos"/>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import TodoCreateForm from 'src/components/TodoCreateForm.vue';
import TodoList from 'src/components/TodoList.vue';



export default defineComponent({
    name: "IndexPage",
    components: {TodoCreateForm, TodoList},
    
    data() {
        return {
            todos: [],
        };
    },
    methods:{
      createTodo(name){
        console.log('name', name);
        this.todos.push({
          id: Date.now(),
          name: name,
        })
    }
  }
})

</script>
