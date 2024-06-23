<template>
    <label v-if="label" :for=id class="field-label">{{ label }}</label>
    <input  
    :value="modelValue" 
    @input="$emit('update:modelValue', $event.target.value)"
    v-bind="$attrs"
    :placeholder="placeholder"
    :id="id"
    class="field-input"
    />
</template>

<script setup>
  const props = defineProps({
    label: {
      type: [String, Boolean],
      default: false,
    },
    modelValue: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      default: '',
    },
    id: {
      type: String,
      default: '',
    }
  });
</script>

<style scoped>
  .field-label {
    display: inline-block;
  }
  .field-input {
    appearance: none;
    background-clip: padding-box;
    background-color: var(--color-white);
    border-radius: 0.375rem;
    border: 1px solid var(--color-grey);
    color: var(--color-black);
    display: block;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    padding: .375rem .75rem;
    transition: border-color .15s ease-in-out, box-shadow .15s ease-in-out;
    width: 100%;
  }
</style>