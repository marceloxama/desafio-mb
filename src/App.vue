<template>
  <div>
    <div>Etapa <span class="step-form--stage">Passo atual</span> de 4</div>
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
</script>