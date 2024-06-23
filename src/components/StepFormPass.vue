<template>
    <div>
      <h2>Passo 3</h2>
      <form @submit.prevent="nextStep">
        <label for="password">Senha:</label>
        <input type="password" v-model="form.password" required />
        <button type="button" @click="prevStep">Voltar</button>
        <button type="submit">Continuar</button>
      </form>
    </div>
  </template>
  
  <script setup>
    const props = defineProps(['form', 'prevStep', 'nextStep']);
  </script>
  