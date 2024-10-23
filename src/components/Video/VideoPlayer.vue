<script setup>
const props = defineProps({
    videosrc: String,
});
</script>

<template>
    <div class="player">
        <video loop autoplay muted :src="videosrc"></video>
        <div class="player__controls">
            <a href="#" @click.prevent="$emit('prevVideo')">⬆️</a>
            <a href="#" @click.prevent="$emit('nextVideo')">⬇️</a>
        </div>
    </div>
</template>

<style scoped>
.player {
    background-image: url('/thumb.png');
    background-repeat: no-repeat;
    background-size: cover;
    display: flex;
    justify-content: center;
    gap: 2rem;
}

.player__controls {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 1rem;
}
</style>