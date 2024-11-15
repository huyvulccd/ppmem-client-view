<template>
  <div class="checkbox-wrapper">
    <input
      type="checkbox"
      :id="id"
      :checked="modelValue"
      @change="updateValue($event.target.checked)"
      :disabled="disabled"
    />
    <label :for="id">{{ label }}</label>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, defineEmits } from 'vue'

interface Props {
  modelValue: boolean
  label: string
  disabled?: boolean
  id?: string
}

defineProps<Props>()
const emits = defineEmits(['update:modelValue'])

// Hàm để cập nhật giá trị của checkbox
const updateValue = (value: boolean) => {
  emits('update:modelValue', value)
}
</script>

<style scoped>
.checkbox-wrapper {
  display: flex;
  align-items: center;
}

input[type="checkbox"] {
  width: 20px;
  height: 20px;
  margin-right: 10px;
  cursor: pointer;
}

input[type="checkbox"]:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

label {
  font-size: 1rem;
  color: #333;
}
</style>
