<script setup>
import { Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});
</script>

<template>
    <div
        class="min-h-screen bg-gray-50 text-black/50 dark:bg-black dark:text-white/50"
        style="background: url('images/logo.png') no-repeat center center; background-size: 400px;"
    >
        <!-- Upper-right login/register buttons -->
        <div class="absolute top-4 right-4 flex gap-2">
            <template v-if="canLogin">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="rounded-md px-2 py-1 text-sm text-black bg-white ring-1 ring-transparent transition hover:bg-gray-200 hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:bg-gray-800 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    Dashboard
                </Link>
                <template v-else>
                    <Link
                        :href="route('login')"
                        class="rounded-md px-2 py-1 text-sm text-black bg-white ring-1 ring-transparent transition hover:bg-gray-200 hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:bg-gray-800 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Log in
                    </Link>
                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="rounded-md px-2 py-1 text-sm text-black bg-white ring-1 ring-transparent transition hover:bg-gray-200 hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:bg-gray-800 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Register
                    </Link>
                </template>
            </template>
        </div>

        <!-- Centered content -->
        <div class="flex min-h-screen items-center justify-center"></div>
    </div>
</template>
