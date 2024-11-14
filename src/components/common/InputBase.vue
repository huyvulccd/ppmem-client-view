<template>
    <div>
        <label for="">{{ content }}</label>
        <input :id="content" :type="type" v-bind="$attrs" />
    </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
defineProps({
    content: {
        type: String,
        required: true
    },
    type: {
        type: String,
        default: 'text',
        required: true
    }
})
</script>
