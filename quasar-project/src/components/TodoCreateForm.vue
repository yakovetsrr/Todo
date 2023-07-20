<template>
    <q-form class="form"
            @submit="handleCreate">
        <q-input v-model="input" outlined label="InputValue: "/>
        <div>
            <q-btn label="Create" type="submit"/>
        </div>
    </q-form>
</template>
<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: "TodoCreateForm",
    emits:['submit'],
    data(){
        return{
            input: '',
        };
    },
    methods:{
        handleCreate(){
            this.$emit('submit', this.input)
        }
    }
})
</script>
<style scoped>
.form{
    max-width: 500px;
}
</style>