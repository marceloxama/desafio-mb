<template>
    <div>
      <h2>Passo 1</h2>
      <form @submit.prevent="nextStep">
        <BaseInput id="email" v-model="form.email" type="email" label="Email:" placeholder="Seu melhor email" required />
        <div>
            <div class="radio-container">
                <input v-model="form.entityType" value="individual" class="radio-input" type="radio" name="entityType" id="individual" checked required>
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
        
        <button type="submit">Continuar</button>
      </form>
    </div>
  </template>
  
  <script setup>
    import BaseInput from './inputs/BaseInput.vue';
    const props = defineProps(['form', 'nextStep']);
  </script>
  