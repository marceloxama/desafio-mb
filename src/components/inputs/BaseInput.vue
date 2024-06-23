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
<script>
    export default {
      data () {
        return {
          id: null
        }
      }, 
      mounted(){
        this.id = this.$.uid
      }
    }
</script>