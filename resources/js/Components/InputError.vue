<template>
    <div v-show="message">
            {{ message }}
    </div>
</template>

<script setup>
defineProps(['message']);
</script>
