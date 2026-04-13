<template>
    <section v-bind="$attrs" class="w-full min-h-screen bg-[#0A0A0A] py-16 px-4 sm:px-6 md:py-20 flex flex-col items-center justify-center font-sans">
        
        <div class="flex flex-col items-center mb-12 md:mb-16 text-center w-full max-w-2xl">
            <div class="inline-flex items-center gap-3 bg-white/5 backdrop-blur-xl border border-white/10 rounded-full px-4 sm:px-6 py-2 mb-4 shadow-2xl">
                <span class="text-[10px] font-black tracking-[5px] uppercase text-red-500">Get In Touch</span>
            </div>
            <h2 class="text-3xl sm:text-4xl md:text-5xl font-light text-white tracking-tight leading-tight">
                Let's work <span class="text-red-500 font-bold italic">together.</span>
            </h2>
            <p class="mt-4 text-sm sm:text-base text-gray-400 max-w-md">
                Have a project in mind or need help with server administration? Drop a message below.
            </p>
        </div>

        <Transition name="fade">
            <div v-if="showSuccess" class="mb-6 w-full max-w-4xl p-4 bg-green-500/10 border border-green-500/50 rounded-2xl text-green-400 text-sm text-center animate-pulse">
                ✓ Message sent! I'll get back to you soon.
            </div>
        </Transition>

        <div class="w-full max-w-4xl grid grid-cols-1 md:grid-cols-5 gap-6 md:gap-8 relative">
            <div class="absolute -top-10 -left-10 w-40 h-40 sm:w-64 sm:h-64 bg-red-600/10 blur-[90px] sm:blur-[100px] rounded-full pointer-events-none"></div>

            <div class="md:col-span-2 space-y-4 sm:space-y-6 order-2 md:order-1">
                <div v-for="info in contactInfo" :key="info.label" 
                    class="p-5 sm:p-6 rounded-3xl border border-white/5 bg-white/[0.02] hover:bg-white/[0.05] transition-colors group"
                >
                    <p class="text-xs font-bold text-red-500 uppercase tracking-widest mb-1">{{ info.label }}</p>
                    <p class="text-sm sm:text-base text-white font-medium group-hover:text-red-400 transition-colors break-words">{{ info.value }}</p>
                </div>
            </div>

            <form @submit.prevent="handleSubmit" class="md:col-span-3 order-1 md:order-2 bg-[#111111] border border-white/10 rounded-[28px] sm:rounded-[32px] p-5 sm:p-8 md:p-10 shadow-2xl relative overflow-hidden">
                <div class="absolute top-0 right-0 w-24 h-24 sm:w-32 sm:h-32 bg-white/[0.02] rotate-45 translate-x-8 sm:translate-x-10 -translate-y-8 sm:-translate-y-10"></div>

                <div class="space-y-5 sm:space-y-6 relative z-10">
                    <div class="grid grid-cols-1 gap-6">
                        <div class="space-y-2">
                            <label class="text-[10px] uppercase tracking-widest text-gray-500 font-bold ml-1">Full Name</label>
                            <input v-model="form.name" type="text" placeholder="John Doe" required
                                class="w-full bg-white/5 border border-white/10 rounded-2xl px-4 sm:px-6 py-3 sm:py-4 text-sm sm:text-base text-white placeholder:text-gray-600 focus:outline-none focus:border-red-500/50 focus:ring-1 focus:ring-red-500/50 transition-all"
                            />
                        </div>

                        <div class="space-y-2">
                            <label class="text-[10px] uppercase tracking-widest text-gray-500 font-bold ml-1">Email Address</label>
                            <input v-model="form.email" type="email" placeholder="john@example.com" required
                                class="w-full bg-white/5 border border-white/10 rounded-2xl px-4 sm:px-6 py-3 sm:py-4 text-sm sm:text-base text-white placeholder:text-gray-600 focus:outline-none focus:border-red-500/50 focus:ring-1 focus:ring-red-500/50 transition-all"
                            />
                        </div>

                        <div class="space-y-2">
                            <label class="text-[10px] uppercase tracking-widest text-gray-500 font-bold ml-1">Message</label>
                            <textarea v-model="form.message" rows="4" placeholder="Tell me about your project..." required
                                class="w-full bg-white/5 border border-white/10 rounded-2xl px-4 sm:px-6 py-3 sm:py-4 text-sm sm:text-base text-white placeholder:text-gray-600 focus:outline-none focus:border-red-500/50 focus:ring-1 focus:ring-red-500/50 transition-all resize-none min-h-[140px]"
                            ></textarea>
                        </div>
                    </div>

                    <button type="submit" :disabled="isSubmitting"
                        class="w-full bg-red-600 hover:bg-red-500 text-white text-sm sm:text-base font-bold py-3.5 sm:py-4 rounded-2xl transition-all duration-300 transform hover:scale-[1.02] active:scale-[0.98] disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center gap-3 shadow-[0_10px_30px_rgba(220,38,38,0.3)]"
                    >
                        <span>{{ isSubmitting ? 'Sending...' : 'Send Message' }}</span>
                        <svg v-if="!isSubmitting" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="m22 2-7 20-4-9-9-4Z"/><path d="M22 2 11 13"/>
                        </svg>
                    </button>
                </div>
            </form>
        </div>
    </section>
</template>

<script setup>
    import { ref, reactive } from 'vue'
    import emailjs from '@emailjs/browser';

    // Disabling inheritance allows us to manually bind attributes via v-bind="$attrs"
    defineOptions({
    inheritAttrs: false
    })

    const isSubmitting = ref(false)
    const showSuccess = ref(false)

    const contactInfo = [
        { label: 'Email Me', value: 'vprogrammer11@gmail.com' },
        { label: 'Location', value: 'Surigao City, Philippines' },
        { label: 'Availability', value: 'Open for Freelance' }
    ]

    const form = reactive({
        name: '',
        email: '',
        message: ''
    })

    const handleSubmit = async () => {
        isSubmitting.value = true;

        const SERVICE_ID = 'service_t99aykp'; 
        const TEMPLATE_ID = 'template_0vsjeoh';
        const PUBLIC_KEY = 'IO2R6pfdCf4AijTba';

        const templateParams = {
            from_name: form.name,
            from_email: form.email,
            to_name: 'VProgrammer',
            message: form.message,
            reply_to: form.email
        };

        try {
            await emailjs.send(SERVICE_ID, TEMPLATE_ID, templateParams, PUBLIC_KEY);
            showSuccess.value = true;
            form.name = '';
            form.email = '';
            form.message = '';
            setTimeout(() => { showSuccess.value = false }, 5000);
        } catch (error) {
            console.error('EMAILJS ERROR:', error);
            alert('Failed to send message.');
        } finally {
            isSubmitting.value = false;
        }
    };
</script>

<style scoped>
    .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s ease;
    }
    .fade-enter-from, .fade-leave-to {
    opacity: 0;
    }
</style>
