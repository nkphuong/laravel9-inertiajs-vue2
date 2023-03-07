<template>
    <div class="d-flex flex-column page page-center">
        <div class="container container-tight py-4">
            <div class="text-center mb-4">
            <Link href="/" class="navbar-brand navbar-brand-autodark">
                <ApplicationLogo height="36"  />
            </Link>
            </div>
            <slot />
        </div>
    </div>
</template>
<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import {Link} from "@inertiajs/vue3";
</script>
