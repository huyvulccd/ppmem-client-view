<template>
    <button
      :class="[
        'base-button',
        sizeClass,
        colorClass,
        { 'button-outline': outline },
        { 'button-disabled': disabled }
      ]"
      :disabled="disabled"
      :id="id"
    >
      <slot />
    </button>
  </template>
  
  <script lang="ts" setup>
  import { defineProps } from 'vue'
  import { computed } from "vue";

  interface ButtonProps {
    color?: 'primary' | 'secondary' | 'success' | 'danger';
    size?: 'small' | 'medium' | 'large';
    outline?: boolean;
    disabled?: boolean;
    id?: string;
  }
  
  const props = defineProps<ButtonProps>()
  
  // Xác định các lớp tùy thuộc vào props
  const sizeClass = computed(() => {
    switch (props.size) {
      case 'small': return 'button-small'
      case 'large': return 'button-large'
      default: return 'button-medium'
    }
  })
  
  const colorClass = computed(() => {
    return `button-${props.color || 'primary'}`
  })
  </script>
  
  <style scoped>
  /* Các lớp cơ bản cho button */
  .base-button {
    padding: 10px 20px;
    font-size: 1rem;
    font-weight: 500;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease, color 0.3s ease;
    border: none;
  }
  
  .button-outline {
    background-color: transparent;
    border: 2px solid currentColor;
  }
  
  /* Kích thước button */
  .button-small {
    font-size: 0.8rem;
    padding: 5px 10px;
  }
  
  .button-medium {
    font-size: 1rem;
    padding: 10px 20px;
  }
  
  .button-large {
    font-size: 1.2rem;
    padding: 15px 25px;
  }
  
  /* Màu sắc button */
  .button-primary {
    background-color: #1877f2;
    color: white;
    font-weight: bold;
  }
  .button-primary.button-outline {
    color: #1877f2;;
  }
  
  .button-secondary {
    background-color: #6c757d;
    color: white;
  }
  .button-secondary.button-outline {
    color: #6c757d;
  }
  
  .button-success {
    background-color: #28a745;
    color: white;
  }
  .button-success.button-outline {
    color: #28a745;
  }
  
  .button-danger {
    background-color: #dc3545;
    color: white;
  }
  .button-danger.button-outline {
    color: #dc3545;
  }
  
  /* Button khi bị disabled */
  .button-disabled {
    background-color: #e0e0e0;
    color: #a0a0a0;
    cursor: not-allowed;
  }
  </style>
  