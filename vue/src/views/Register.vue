<template>
    <div>
        <div>
            <img
                class="mx-auto h-12 w-auto"
                src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
                alt="Workflow"
            />
            <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-900">
                Register for free
            </h2>
            <p class="mt-2 text-center text-sm text-gray-600">
                Or
                {{ " " }}
                <a
                    href="#"
                    class="font-medium text-indigo-600 hover:text-indigo-500"
                >
                    start your 14-day free trial
                </a>
            </p>
        </div>
        <form class="mt-8 space-y-6" @submit="register">
            <div class="rounded-md shadow-sm -space-y-px">
                <div>
                    <label for="email-address" class="sr-only">Full Name</label>
                    <input
                        id="name"
                        name="name"
                        type="text"
                        autocomplete="name"
                        required=""
                        class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                        placeholder="Full name"
                        v-model="user.name"
                    />
                </div>
                <div>
                    <label for="email-address" class="sr-only"
                        >Email address</label
                    >
                    <input
                        id="email-address"
                        name="email"
                        type="email"
                        autocomplete="email"
                        required=""
                        class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                        placeholder="Email address"
                        v-model="user.email"
                    />
                </div>
                <div>
                    <label for="password" class="sr-only">Password</label>
                    <input
                        id="password"
                        name="password"
                        type="password"
                        autocomplete="current-password"
                        required=""
                        class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                        placeholder="Password"
                        v-model="user.password"
                    />
                </div>
                <div>
                    <label for="password_confirmation" class="sr-only"
                        >Password_confirmation</label
                    >
                    <input
                        id="password_confirmation"
                        name="password_confirmation"
                        type="password_confirmation"
                        autocomplete="current-password_confirmation"
                        required=""
                        class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 focus:z-10 sm:text-sm"
                        placeholder="Password confirmation"
                        v-model="user.password_confirmation"
                    />
                </div>
            </div>

            <div>
                <button
                    type="submit"
                    class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                >
                    <span
                        class="absolute left-0 inset-y-0 flex items-center pl-3"
                    >
                        <LockClosedIcon
                            class="h-5 w-5 text-indigo-500 group-hover:text-indigo-400"
                            aria-hidden="true"
                        />
                    </span>
                    Sign Up
                </button>
            </div>
        </form>
    </div>
</template>

<script setup>
import { LockClosedIcon } from "@heroicons/vue/solid";
import { store } from "vuex";
import { useRoute } from "vue-router";
import router from "../router";

const router = useRoute();
const user = {
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
};

function register(e) {
    e.preventDefault();
    store.dispatch("register", user).then(() => {
        router.push({
            name: "Dashboard",
        });
    });
}
</script>
