<template>
    <div>
      <h1 class="page-title">Seja bem vindo(a)</h1>
      <form @submit.prevent="nextStep">
        <BaseInput
          v-model="form.email"
          :component-data="emailComponent"
          required
        />
        <div>
            <div class="radio-container">
                <input v-model="form.entityType" value="individual" class="radio-input" type="radio" name="entityType" id="individual" required>
                <label class="radio-label" for="individual">
                    Pessoa física 
                </label>
            </div>
            <div class="radio-container">
                <input v-model="form.entityType" value="company" class="radio-input" type="radio" name="entityType" id="company">
                <label class="radio-label" for="company">
                    Pessoa jurídica
                </label>
            </div>
        </div>
        <div class="button-container">
          <button class="btn btn-primary" type="submit">Continuar</button>
        </div>        
      </form>
    </div>
  </template>
  
  <script setup>
    import { ref } from 'vue';
    import BaseInput from './inputs/BaseInput.vue';
    const props = defineProps(['form', 'nextStep']);

    const emailComponent = ref({
      id: 'email',
      type: 'email',
      placeholder: 'Insira o seu email',
      label: 'Email',
      errorMessage: 'Endereço de email inválido',
      pattern: '^[\\w-\\.]+@([\\w-]+\\.)+[\\w-]{2,4}$',
      minLength: 3,
      maxLength: 40,
    });
  </script>
  