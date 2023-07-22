<template>
  <TodoForm @submit="handleCreate" button-label="Create" />
</template>
<script>
import { defineComponent } from 'vue'
import TodoForm from "components/TodoForm.vue";

export default defineComponent({
    name: "TodoCreateForm",
    components: {TodoForm},
    emits:['submit'],
    methods:{
        handleCreate(name){
            this.$emit('submit', name)
        }
    }
})
</script>
<style scoped>
.form{
    max-width: 500px;
}
</style>
