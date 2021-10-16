<template>
  
  <div v-show="show" class=" bg-black bg-opacity-30 absolute top-0 left-0 w-full h-full flex justify-center z-50">
    <div>{{ description.name }}</div>
    <div class="bg-white self-center w-1/2 h-2/6 p-10 rounded-md drop-shadow-sm text-lg">
       <div class="container gap-6 max-w-md mx-auto rounded-full flex flex-col items-center bg-white h-12">
         <h1 class="text-3xl" >Digite seus dados</h1>
         <input :class="[{'border-red-500': errorName}, 'container border border-black']" type="text" placeholder="Digite seu nome" v-model="description.name" @input="checkErrors">
         <input class="container border border-black" type="number" placeholder="Telefone" v-model="description.fone">
         <input class="container border border-black" type="email" placeholder="E-mail" v-model="description.email">
       </div>
       <div class="flex flex-1 justify-end text-base mt-40 ">
        <AppButton class="text-green-500 hover:bg-green-500 hover:text-white" @click="save">Salvar</AppButton>
        <AppButton class="text-red-500 hover:bg-red-500 hover:text-white" @click="$emit('close')">Fechar</AppButton>
       </div>
       <div>{{ description.name }}</div>
    </div>
   
  </div>
  
</template>

<script setup>
import AppButton from "./AppButton.vue"
</script>

<script>
export default {
  props: ["show"],

  data() {
    return{
       data: [],
       description: {
         name: "",
         fone: "",
         email: "",
       },
       errorName: false,
       errorNumber: false,
       errorEmail: false,
       
    }
  },
  methods: {
     save(){
       this.checkErrors()
       this.$emit("saved", this.description)
       this.$emit("close")
     },

     checkErrors(){
       if(!this.description.name) this.errorName = true
       else this.errorName = false
     }
    
  },
};
</script>
