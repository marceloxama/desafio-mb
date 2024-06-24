<template>
    <div>
      <label :for=props.componentData.id class="field-input__label">{{ props.componentData.label }}</label>
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
        class="field-input__error"
        v-if="requiredError"
      >
        {{ requiredError  }}
      </div>
    </div>
</template>

<script setup>
  import { ref } from 'vue'

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