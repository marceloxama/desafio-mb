<template>
    <div>
      <h1 class="page-title">Senha de acesso</h1>
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
      errorMessage: 'Mínimo de 8 caracteres',
      pattern: '',
      minLength: 6,
      maxLength: 30
    });
  </script>
  <script>
    export default {
      data() {
        return {
          showPassword: false,
          password: null
        };
      },
      computed: {
        buttonLabel() {
          return (this.showPassword) ? "Hide" : "Show";
        }
      },
      methods: {
        toggleShow() {
          this.showPassword = !this.showPassword;
        }
      }
    };
  </script>
  