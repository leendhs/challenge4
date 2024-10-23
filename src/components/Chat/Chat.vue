<script setup>
    import ChatMessages from './ChatMessages.vue';
    import ChatForm from './ChatForm.vue';
    import { reactive, onMounted } from 'vue'; 

    const messages = reactive([]);

    onMounted(() => {
    fetch("https://zero3-mongodb-challenge.onrender.com/api/v1/messages")
        .then((response) => response.json())
        .then((data) => {
            messages.push(...data.data.messages.reverse());
        });
    });

    function addMessage(newMessage) {
        messages.unshift(newMessage);
    }

</script>

<template>
    <ChatMessages :messages="messages" />
    <ChatForm @submitMessage="addMessage" />
</template>

<style scoped>

</style>