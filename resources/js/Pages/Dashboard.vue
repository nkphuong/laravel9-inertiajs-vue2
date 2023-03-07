<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            Dashboard
        </template>
        <div class="page-body">
            <div class="container-xl">

                <div class="alert alert-success">
                    <div class="alert-title">
                        Welcome {{ $page.props.auth.user.name }}
                    </div>
                    <div class="text-muted">
                        You are logged in!
                    </div>
                </div>

            </div>
        </div>
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import { Head } from '@inertiajs/vue3';
</script>
