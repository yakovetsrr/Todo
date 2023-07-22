<template>
  <div :class="{ completed: todo.completed }">
    <span v-if="!isEditable" @click="handleCompleted">{{ todo.name }}</span>
    <EditTodoForm v-else :name="todo.name" @submit="handleEdit"/>
    <div>
      <q-btn color="deep-orange" glossy label="Delete" @click="showConfirmDeleteDialog"/>
      <q-btn color="secondary" glossy label="Edit" @click="isEditable=!isEditable"/>
    </div>
    <q-dialog v-model="confirmDeleteDialogVisible" persistent>
      <q-card>
        <q-card-section class="row items-center">
          <span class="q-ml-sm">Точно удалить {{todo.name}}?</span>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Отмена" color="primary" v-close-popup />
          <q-btn flat label="Удалить" color="primary" v-close-popup  @click="handleDelete(todo.id)"/>
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>
<script>
import {defineComponent} from 'vue'
import EditTodoForm from "components/EditTodoForm.vue";
export default defineComponent({
  components: {EditTodoForm},
  props:{
    todo:{
      type: Object,
      required: true,
    }
  },
  emits:['remove', 'update', 'completed'],
  data(){
    return{
        isEditable: false,
        confirmDeleteDialogVisible: false
    }
  },
  methods:{
    handleDelete(id){
      this.$emit('remove', id)
    },
    handleEdit(newName){
      console.log(newName);
      this.$emit('update', {
        id: this.todo.id,
        name: newName,
        completed: this.todo.completed,
      })
      this.isEditable = false;
    },
    handleCompleted(){
      this.$emit('completed', this.todo.id)
    },
    showConfirmDeleteDialog() {
      this.confirmDeleteDialogVisible = !this.confirmDeleteDialogVisible;
    }
  },

})
</script>
<style scoped>
.completed{
  text-decoration: line-through;
}
</style>
<script setup lang="ts">
</script>
