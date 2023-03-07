<template>
    <div class="page">
        <div class="sticky-top">
            <Header />
        </div>
        <Navigation />
        <div class="page-wrapper">
            <slot />
        </div>
    </div>

</template>

<script setup>
import Header from '@/Layouts/Header.vue';
import Navigation from '@/Layouts/Navigation.vue';
</script>
