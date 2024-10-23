<script setup>
    import { ref } from 'vue';
    import { defineEmits } from 'vue';

    const emit = defineEmits();
    const messageText = ref('');

    async function postMessage() {
        const newMessage = {
            user: "Emiel",
            text: messageText.value
        };
        
        const response = await fetch("https://zero3-mongodb-challenge.onrender.com/api/v1/messages", {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({ message: newMessage})
        });

        const result = await response.json();

        if (response.ok) {
            emit('submitMessage', newMessage);
            messageText.value = '';
        } else {
            console.error(result.message);
        }
    }
</script>

<template>
    <div class="form">
        <input v-model="messageText" type="text" placeholder="Add comment..." />
        <button @click="postMessage">Send</button>
    </div>
</template>

<style scoped>
.form input {
    padding: .5rem;
}

.form button {
    padding: .5rem;
    cursor: pointer;
}
</style>