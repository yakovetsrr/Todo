<template>
 <TodoForm @submit="handleSubmit" button-label="Edit" :default-input="name"/>
</template>
<script>
import {defineComponent} from 'vue'
import TodoForm from "components/TodoForm.vue";
export default defineComponent({
  components: {TodoForm},

  props:{
    name:{
        type: String,
        required: true,
    }
  },
  emits:["submit"],
  methods:{
    handleSubmit(name){
       this.$emit('submit', name)
    }
  }
  }
)
</script>

<style scoped>
.form{
  max-width: 500px;
}
</style>>
