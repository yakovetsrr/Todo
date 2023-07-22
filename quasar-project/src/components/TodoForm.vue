<template>
  <q-form class="form"
          @submit="handleSubmit">
    <q-input v-model="input" outlined label="InputValue: "/>
    <div>
      <q-btn :label="buttonText" type="submit"/>
    </div>
  </q-form>
</template>

<script>
import {defineComponent} from 'vue'

export default defineComponent({
  name: "TodoForm",
  props:{
    buttonLabel:{
      type: String,
    },
    defaultInput:{
      type:String,
    }
  },
  emits:['submit'],
  data(){
    return{
      input: this.defaultInput,
    };
  },
  computed: {
    buttonText() {
      return this.buttonLabel ?? 'button';
    },
  },
  methods:{
    handleSubmit(){
      this.$emit('submit', this.input)
    }
  }
})
</script>

<style scoped>

</style>
