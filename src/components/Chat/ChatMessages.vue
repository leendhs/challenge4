<script setup>
import { defineProps } from "vue";

const props = defineProps({
    messages: {
        type: Array,
        required: true
    }
});
</script>

<template>
    <h2>Comments</h2>
    <ul>
        <li v-for="message in messages">
            <strong>{{ message.user }}:</strong> {{ message.text }}
        </li>
    </ul>
</template>

<style scoped>

</style>