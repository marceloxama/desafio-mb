<template>
    <div>
      <h2>Passo 2</h2>
      <form @submit.prevent="nextStep">
        <div v-if="form.entityType === 'individual'">
          <BaseInput v-model="form.name" type="text" label="Nome:" placeholder="Insira o seu nome" required />
          <BaseInput v-model="form.cpf" type="text" label="CPF:" required />
          <BaseInput v-model="form.dob" type="date" label="Data de Nascimento:" required />
          <BaseInput v-model="form.personalPhone" type="tel" label="Telefone:" required />
        </div>
        <div v-if="form.entityType === 'company'">
          <BaseInput v-model="form.company" type="tel" label="Razão Social:" required />
          <BaseInput v-model="form.cnpj" type="tel" label="CNPJ:" required />
          <BaseInput v-model="form.openingDate" type="tel" label="Data de Abertura:" required />
          <BaseInput v-model="form.professionalPhone" type="tel" label="Telefone:" required />
        </div>
        <button type="button" @click="prevStep">Voltar</button>
        <button type="submit">Continuar</button>
      </form>
    </div>
  </template>
  
  <script setup>
    import BaseInput from './inputs/BaseInput.vue';
  
    const props = defineProps(['form', 'prevStep', 'nextStep']);
  </script>
  