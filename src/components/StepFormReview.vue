<template>
    <div>
      <h2>Passo 4</h2>
      <div>
        <p>Email: {{ form.email }}</p>
        <div v-if="form.entityType === 'individual'">
          <p>Nome: {{ form.name }}</p>
          <p>CPF: {{ form.cpf }}</p>
          <p>Data de Nascimento: {{ form.dob }}</p>
          <p>Telefone: {{ form.personalPhone }}</p>
        </div>
        <div v-if="form.entityType === 'company'">
          <p>Razão Social: {{ form.company }}</p>
          <p>CNPJ: {{ form.cnpj }}</p>
          <p>Data de Abertura: {{ form.openingDate }}</p>
          <p>Telefone: {{ form.professionalPhone }}</p>
        </div>
        <p>Senha: {{ form.password }}</p>
      </div>
      <button @click="prevStep">Voltar</button>
      <button @click="submitForm">Cadastrar</button>
    </div>
  </template>
  
  <script setup>
    const props = defineProps(['form', 'prevStep', 'submitForm']);
  </script>
  