<template>
    <div class="input-wrapper">
      <label v-if="label">{{ label }}</label>
      <input
        :type="type"
        :placeholder="placeholder"
        :value="modelValue"
        @input="updateValue($event.target.value)"
        :class="['input-field', { 'input-disabled': disabled }]"
        :disabled="disabled"
      />
      <slot/> <!-- Chèn nội dung bổ sung vào nếu cần -->
    </div>
  </template>
  
  <script lang="ts" setup>
  import { defineProps, defineEmits } from 'vue'
  
  interface Props {
    type?: string
    placeholder?: string
    modelValue?: string
    disabled?: boolean
    label?: string
  }
  
defineProps<Props>()
  const emits = defineEmits(['update:modelValue'])
  
  // Hàm để cập nhật giá trị của input
  const updateValue = (value: string) => {
    emits('update:modelValue', value)
  }
  </script>
  
  <style scoped>
  .input-wrapper {
    display: flex;
    flex-direction: column;
  }
  
  label {
    font-size: 0.9rem;
    margin-bottom: 5px;
    color: #333;
  }
  
  .input-field {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
    transition: border-color 0.3s;
  }
  
  .input-field:focus {
    border-color: #007bff;
    outline: none;
  }
  
  .input-disabled {
    background-color: #f0f0f0;
    color: #a0a0a0;
    cursor: not-allowed;
  }
  </style>
  