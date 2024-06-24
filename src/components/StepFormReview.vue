<template>
    <div>
      <h2>Passo 4</h2>
      <form @submit.prevent="submitForm">
        <div>
          <div class="field-container">
            <label class="field-input__label">Email</label>
            <input 
              class="field-input"
              v-model="form.email"
              type="text"
              disabled
            />
          </div>
          <div v-if="form.entityType === 'individual'">
            <div class="field-container">
              <label class="field-input__label">Nome</label>
                <input
                  class="field-input" 
                  v-model="form.name"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">CPF</label>
                <input 
                  class="field-input"
                  v-model="form.cpf"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">Data de Nascimento</label>
                <input 
                class="field-input"
                  v-model="form.dob"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">Telefone</label>
                <input 
                class="field-input"
                  v-model="form.personalPhone"
                  type="text"
                  disabled
                />
            </div>
          </div>
          <div v-if="form.entityType === 'company'">
            <div class="field-container">
              <label class="field-input__label">Razão Social:</label>
                <input 
                class="field-input"
                  v-model="form.company"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">CNPJ</label>
                <input 
                class="field-input"
                  v-model="form.cnpj"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">Data de Abertura</label>
                <input 
                class="field-input"
                  v-model="form.openingDate"
                  type="text"
                  disabled
                />
            </div>
            <div class="field-container">
              <label class="field-input__label">Telefone</label>
                <input 
                class="field-input"
                  v-model="form.companyPhone"
                  type="text"
                  disabled
                />
            </div>
          </div>
          <div class="field-container">
            <label class="field-input__label">Senha</label>
              <input 
              class="field-input"
                v-model="form.password"
                type="text"
                disabled
              />
          </div>
        </div>
        <div class="button-container">
          <button class="btn btn-outline-primary" @click="prevStep">Voltar</button>
          <button class="btn btn-primary" type="submit">Cadastrar</button>
        </div>
        
      </form>
    </div>
  </template>
  
  <script setup>
    const props = defineProps(['form', 'prevStep', 'submitForm']);
  </script>
  