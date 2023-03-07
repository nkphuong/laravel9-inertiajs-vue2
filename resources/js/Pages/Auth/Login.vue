<template>
    <Head title="Log in" />

    <GuestLayout>


        <div v-if="status" class="mb-4 text-sm font-medium text-green-600">
            {{ status }}
        </div>

        <form @submit.prevent="submit" class="card card-md">
            <div class="card-body">
                <h2 class="card-title text-center mb-4">Login to your account</h2>
                <div class="mb-3">
                    <label class="form-label">Email address</label>
                    <TextInput id="email" type="email" class="form-control" :class="{'is-invalid':form.errors.email}" v-model="form.email" required autofocus autocomplete="username" />
                    <InputError class="invalid-feedback" :message="form.errors.email" />
                </div>

                <div class="mb-2">
                    <label class="form-label">
                        Password
                        <span class="form-label-description">
                            <a :href="route('password.request')" tabindex="5">Forgot Password?</a>
                        </span>
                    </label>
                    <div class="input-group input-group-flat">
                        <TextInput id="password" type="password"  class="form-control" :class="{'is-invalid':form.errors.password}"  v-model="form.password" required autocomplete="current-password" />
                        <span class="input-group-text">
                    <a href="#" class="link-secondary" data-bs-toggle="tooltip" aria-label="Show password" data-bs-original-title="Show password"><!-- Download SVG icon from http://tabler-icons.io/i/eye -->
                      <svg xmlns="http://www.w3.org/2000/svg" class="icon" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M12 12m-2 0a2 2 0 1 0 4 0a2 2 0 1 0 -4 0"></path><path d="M22 12c-2.667 4.667 -6 7 -10 7s-7.333 -2.333 -10 -7c2.667 -4.667 6 -7 10 -7s7.333 2.333 10 7"></path></svg>
                    </a>
                  </span>
                    </div>

                    <InputError class="invalid-feedback" :message="form.errors.password" />
                </div>
                <div class="mb-2">
                    <label class="form-check">
                        <Checkbox type="checkbox" class="form-check-input" tabindex="3" name="remember" />
                        <span class="form-check-label">Remember me on this device</span>
                    </label>
                </div>

                <div class="form-footer">
                <PrimaryButton class="btn btn-primary w-100" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Log in
                </PrimaryButton>
                </div>
            </div>
        </form>
    </GuestLayout>
</template>

<script setup>

import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: Boolean,
    status: String,
});

const form = useForm({
    email: '',
    password: '',
    remember: false
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>
