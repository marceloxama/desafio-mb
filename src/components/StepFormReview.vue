<template>
    <h1>Passo 4</h1>
    <div>
        <button @click="prevStep">Voltar</button>
        <button @click="submitForm">Cadastrar</button>
    </div>
</template>

<script setup>
    const props = defineProps(['form', 'prevStep', 'submitForm']);
</script>