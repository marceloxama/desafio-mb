<template>
    <label :for=props.componentData.id class="field-label">{{ props.componentData.label }}</label>
    <input
      :id="props.componentData.id"
      class="field-input"
      :value="modelValue"
      v-bind="$attrs"
      :type="props.componentData.type"
      :placeholder="props.componentData.placeholder"
      @input="onInput"
      @blur="fieldValidade"
    />
    <div
      class="error-message"
      v-if="requiredError"
    >
      {{ requiredError  }}
    </div>
</template>

<script setup>
  import { defineProps, defineEmits, ref } from 'vue'

  const props = defineProps({
    modelValue: {
      required: true
    },
    componentData: {
      type: Object,
      default: () => {
        return {
          id: null,
          type: 'text',
          placeholder: 'Placeholder',
          label: 'Label',
          errorMessage: null,
          pattern: '',
          minLength: null,
          maxLength: null
        }
      }
    }
  })

  const emit = defineEmits(['update:modelValue', 'form-validate'])

  const onInput = (value) => {
    emit('update:modelValue', value.target.value)
  }

  const fieldValidade = (event) => {
    const isPatternValid = props.componentData.pattern ? !!event.target.value.match(props.componentData.pattern) : true
    const isLengthValid = event.target.value.length >= props.componentData.minLength && event.target.value.length <= props.componentData.maxLength

    if(!isPatternValid || !isLengthValid) {
      requiredError.value = props.componentData.errorMessage
    } else {
      requiredError.value = ''
    }
  }

  const requiredError = ref('')

</script>

<style scoped>
  .field-label {
    display: inline-block;
    margin-bottom: 5px;
    font-weight: 600;
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
    margin-bottom: 16px;
    padding: .375rem .75rem;
    transition: border-color .15s ease-in-out, box-shadow .15s ease-in-out;
    width: 100%;
  }
  .error-message {
    color: var(--color-red);
    margin: -16px 0 10px;
  }
</style>