<template>
    <h1>Passo 3</h1>
    <form @submit.prevent="nextStep">
        <button type="button" @click="prevStep">Voltar</button>
        <button type="submit">Continuar</button>
    </form>
</template>

<script setup>
    const props = defineProps(['form', 'prevStep', 'nextStep']);
</script>