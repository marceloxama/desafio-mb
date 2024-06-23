<template>
    <h1>Passo 1</h1>
    <form @submit.prevent="nextStep">
        <button type="submit">Continuar</button>
    </form>
</template>

<script setup>
    const props = defineProps(['form', 'nextStep']);
</script>