<template>
  <div>
    <div>Etapa <span class="step-form--stage">{{ currentStep+1 }}</span> de {{ steps.length }}</div>
    <component :is="steps[currentStep].step" 
               :form="form" 
               :nextStep="nextStep" 
               :prevStep="prevStep" 
               :submitForm="submitForm" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import StepFormEmail from './components/StepFormEmail.vue';
import StepFormEntity from './components/StepFormEntity.vue';
import StepFormPass from './components/StepFormPass.vue';
import StepFormReview from './components/StepFormReview.vue';

const form = ref({
  email: '',
  entitytype: '',
  name: '',
  cpf: '',
  dob: '',
  personalPhone: '',  
  company: '',
  cnpj: '',
  openingDate: '',
  professionalPhone: '',
  password: '',
});

const currentStep = ref(0);

const steps = [
  { step: StepFormEmail },
  { step: StepFormEntity },
  { step: StepFormPass },
  { step: StepFormReview }
];

const nextStep = () => {
  if (currentStep.value < steps.length - 1) {
    currentStep.value++;
  }
};

const prevStep = () => {
  if (currentStep.value > 0) {
    currentStep.value--;
  }
};

const submitForm = async () => {
  try {
    const response = await fetch('http://localhost:3000/registration', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify(form.value)
    });
    const result = await response.json();
    alert(result.message);
  } catch (error) {
    console.error('Erro ao enviar o formulário:', error);
  }
};

</script>
