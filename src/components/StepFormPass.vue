<template>
    <div>
      <h2>Passo 3</h2>
      <form @submit.prevent="nextStep">
        <BaseInput 
            v-model="form.password"
            :component-data="passComponent"
            required
        />
        <div class="button-container">
          <button class="btn btn-outline-primary" type="button" @click="prevStep">Voltar</button>
          <button class="btn btn-primary" type="submit">Continuar</button>
        </div>
      </form>
    </div>
  </template>
  
  <script setup>
    import { ref } from 'vue';
    import BaseInput from './inputs/BaseInput.vue';
    const props = defineProps(['form', 'prevStep', 'nextStep']);

    const passComponent = ref({
      id: 'pass',
      type: 'password',
      placeholder: 'Insira sua senha',
      label: 'Senha',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 8,
      maxLength: 10
    });
  </script>
  