<template>
    <!-- Added wrapper div for centering -->
    <div
        class="min-h-screen w-full flex items-center justify-center bg-gray-50 py-12 px-4"
    >
        <div
            class="bg-white rounded-lg shadow-xl relative overflow-hidden w-[768px] max-w-full min-h-[480px]"
            :class="{ 'right-panel-active': isRightPanelActive }"
        >
            <!-- Rest of the component remains the same -->
            <!-- Sign Up Container -->
            <div
                class="absolute top-0 h-full transition-all duration-[600ms] left-0 w-1/2 opacity-0 z-1"
                :class="{
                    'transform translate-x-full opacity-100 z-5':
                        isRightPanelActive,
                }"
            >
                <form
                    @submit.prevent="handleSignUp"
                    class="bg-white flex flex-col items-center justify-center px-12 h-full text-center"
                >
                    <h1 class="font-bold m-0 text-4xl">Create Account</h1>
                    <div class="my-5">
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-google-plus-g"></i>
                        </a>
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                    <span class="text-sm"
                        >or use your email for registration</span
                    >
                    <input
                        type="text"
                        v-model="signUpForm.name"
                        placeholder="Name"
                        class="bg-gray-100 border-none rounded-full py-3 px-4 my-2 w-full"
                    />
                    <input
                        type="email"
                        v-model="signUpForm.email"
                        placeholder="Email"
                        class="bg-gray-100 border-none rounded-full py-3 px-4 my-2 w-full"
                    />
                    <input
                        type="password"
                        v-model="signUpForm.password"
                        placeholder="Password"
                        class="bg-gray-100 border-none rounded-full py-3 px-4 my-2 w-full"
                    />
                    <button
                        type="submit"
                        class="rounded-full border border-[#392d69] bg-[#392d69] text-white text-xs font-bold py-3 px-12 uppercase tracking-wider transition duration-[600ms] transform hover:scale-95 cursor-pointer focus:outline-none"
                    >
                        Sign Up
                    </button>
                </form>
            </div>

            <!-- Sign In Container -->
            <div
                class="absolute top-0 h-full transition-all duration-[600ms] left-0 w-1/2 z-2"
                :class="{ 'transform translate-x-full': isRightPanelActive }"
            >
                <form
                    @submit.prevent="handleSignIn"
                    class="bg-white flex flex-col items-center justify-center px-12 h-full text-center"
                >
                    <h1 class="font-bold m-0 text-4xl">Sign in</h1>
                    <div class="my-5">
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-facebook-f"></i>
                        </a>
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-google-plus-g"></i>
                        </a>
                        <a
                            href="#"
                            class="border border-gray-200 rounded-full inline-flex justify-center items-center mx-1 h-10 w-10 transition-all duration-[600ms] hover:bg-[#392d69] hover:text-white"
                        >
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                    </div>
                    <span class="text-sm">or use your account</span>
                    <input
                        id="email"
                        type="email"
                        v-model="form.email"
                        placeholder="Email"
                        class="bg-gray-100 border-none rounded-full py-3 px-4 my-2 w-full"
                        autofocus
                        autocomplete="username"
                    />
                    <input
                        type="password"
                        v-model="form.password"
                        placeholder="Password"
                        class="bg-gray-100 border-none rounded-full py-3 px-4 my-2 w-full"
                        required
                        autocomplete="current-password"
                    />
                    <a href="#" class="text-gray-700 text-sm no-underline my-4"
                        >Forgot your password?</a
                    >
                    <button
                        type="submit"
                        class="rounded-full border border-[#392d69] bg-[#392d69] text-white text-xs font-bold py-3 px-12 uppercase tracking-wider transition duration-[600ms] transform hover:scale-95 cursor-pointer focus:outline-none"
                        :disabled="form.processing"
                    >
                        Sign In
                    </button>
                </form>
            </div>

            <!-- Overlay Container -->
            <div
                class="absolute top-0 left-1/2 w-1/2 h-full overflow-hidden transition transform duration-[600ms] z-100"
                :class="{ '-translate-x-full': isRightPanelActive }"
            >
                <div
                    class="bg-gradient-to-r from-[#392d69] to-[#b57bee] bg-no-repeat bg-cover bg-center text-white relative -left-full h-full w-[200%] transform transition duration-[600ms]"
                    :class="{ 'translate-x-1/2': isRightPanelActive }"
                >
                    <!-- Overlay Left -->
                    <div
                        class="absolute flex items-center justify-center flex-col px-10 text-center top-0 h-full w-1/2 -translate-x-1/5 transition transform duration-[600ms]"
                        :class="{ 'translate-x-0': isRightPanelActive }"
                    >
                        <h1 class="font-bold text-4xl m-0">Welcome Back!</h1>
                        <p
                            class="text-sm font-light leading-5 tracking-wider my-5"
                        >
                            To keep connected with us please login with your
                            personal info
                        </p>
                        <button
                            @click="togglePanel(false)"
                            class="rounded-full border border-white bg-transparent text-white text-xs font-bold py-3 px-12 uppercase tracking-wider transition duration-[600ms] transform hover:scale-95 cursor-pointer focus:outline-none"
                        >
                            Sign In
                        </button>
                    </div>
                    <!-- Overlay Right -->
                    <div
                        class="absolute right-0 flex items-center justify-center flex-col px-10 text-center top-0 h-full w-1/2 transform transition duration-[600ms]"
                        :class="{ 'translate-x-1/5': isRightPanelActive }"
                    >
                        <h1 class="font-bold text-4xl m-0">Hello, Friend!</h1>
                        <p
                            class="text-sm font-light leading-5 tracking-wider my-5"
                        >
                            Enter your personal details and start journey with
                            us
                        </p>
                        <button
                            @click="togglePanel(true)"
                            class="rounded-full border border-white bg-transparent text-white text-xs font-bold py-3 px-12 uppercase tracking-wider transition duration-[600ms] transform hover:scale-95 cursor-pointer focus:outline-none"
                        >
                            Sign Up
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "AuthComponent",
    data() {
        return {
            isRightPanelActive: false,
            signUpForm: {
                name: "",
                email: "",
                password: "",
            },
            form: {
                email: "",
                password: "",
            },
        };
    },
    methods: {
        togglePanel(isActive) {
            this.isRightPanelActive = isActive;
        },
        handleSignUp() {
            console.log("Sign Up:", this.signUpForm);
        },
        handleSignIn() {
            console.log("Sign In:", this.form);
        },
    },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,800");

/* Custom animation classes */
.right-panel-active .sign-up-container {
    animation: show 0.25s;
}

@keyframes show {
    0%,
    49.99% {
        opacity: 0;
        z-index: 1;
    }

    50%,
    100% {
        opacity: 1;
        z-index: 5;
    }
}
</style>
