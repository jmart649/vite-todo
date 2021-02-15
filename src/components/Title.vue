<template>
    <h1 class="text-6xl text-center italic font-bold text-blue-700 underline"> {{ msg }} </h1>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
    msg: {
        type: String,
        default: 'Custom Title',
    },
})
</script>