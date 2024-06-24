<template>
    <div>
      <h2>Passo 2</h2>
      <form @submit.prevent="nextStep">
        <div v-if="form.entityType === 'individual'">
          <BaseInput 
            v-model="form.name"
            :component-data="nameComponent"
            required
           />
          <BaseInput 
            v-model="form.cpf" 
            :component-data="cpfComponent"
            required
           />
          <BaseInput 
            v-model="form.dob"
            :component-data="birthDateComponent"
            :max="today"
            onkeydown="return false"
            required
           />
          <BaseInput 
            v-model="form.personalPhone" 
            :component-data="personalPhoneComponent" 
            required
           />
        </div>
        <div v-if="form.entityType === 'company'">
          <BaseInput 
            v-model="form.company" 
            :component-data="companyNameComponent" 
            required
           />
          <BaseInput 
            v-model="form.cnpj" 
            :component-data="cnpjComponent" 
            required 
          />
          <BaseInput 
            v-model="form.openingDate" 
            :component-data="openDateComponent" 
            required 
          />
          <BaseInput 
            v-model="form.companyPhone" 
            :component-data="companyPhoneComponent" 
            required
           />
        </div>
        <button type="button" @click="prevStep">Voltar</button>
        <button type="submit">Continuar</button>
      </form>
    </div>
  </template>
  
  <script setup>
    import { ref } from 'vue';
    import BaseInput from './inputs/BaseInput.vue';
  
    const props = defineProps(['form', 'prevStep', 'nextStep']);
    
    const nameComponent = ref({
      id: 'personalName',
      type: 'text',
      placeholder: 'Insira o seu nome',
      label: 'Nome',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 2,
      maxLength: 70
    });

    const companyNameComponent = ref({
      id: 'companyName',
      type: 'text',
      placeholder: 'Insira a razão social',
      label: 'Razão social',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 5,
      maxLength: 100
    });

    const cpfComponent = ref({
      id:'cpf',
      type: 'text',
      placeholder: '___.___.___-__',
      label: 'CPF',
      errorMessage: 'CPF inválido',
      pattern: '',
      minLength: 2,
      maxLength: 70
    });

    const cnpjComponent = ref({
      id:'cnpj',
      type: 'text',
      placeholder: '___.___.___/____-__',
      label: 'CNPJ',
      errorMessage: 'CNPJ inválido',
      pattern: '',
      minLength: 19,
      maxLength: 19
    });

    const birthDateComponent = ref({
      id: 'birthday',
      type: 'date',
      placeholder: '',
      label: 'Data de nascimento',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 10,
      maxLength: 10
    });

    const openDateComponent = ref({
      id: 'openDate',
      type: 'date',
      placeholder: '',
      label: 'Data de abertura',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 10,
      maxLength: 10
    });

    const personalPhoneComponent = ref({
      id: 'personalPhone',
      type: 'text',
      placeholder: '(xx)xxxxx-xxxx',
      label: 'Celular',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 13,
      maxLength: 14
    });

    const companyPhoneComponent = ref({
      id: 'companyPhone',
      type: 'text',
      placeholder: '(xx)xxxxx-xxxx',
      label: 'Telefone',
      errorMessage: 'Campo obrigatório',
      pattern: '',
      minLength: 13,
      maxLength: 14
    });
  </script>
  
  