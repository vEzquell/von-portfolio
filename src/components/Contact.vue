<template>
    <section v-bind="$attrs" class="section-shell relative rounded-[34px] px-4 py-12 sm:px-6 sm:py-14 md:px-8">
        <div class="ambient-orb left-[-4rem] top-12 h-44 w-44 bg-red-600/[0.16]"></div>
        <div class="ambient-orb right-[-4rem] bottom-14 h-48 w-48 bg-orange-400/10 [animation-delay:2s]"></div>

        <div class="relative z-10">
            <div class="mx-auto max-w-3xl text-center">
                <div class="section-kicker mx-auto">
                    <span class="h-2 w-2 rounded-full bg-red-500"></span>
                    Get In Touch
                </div>
                <h2 class="section-title mt-5">Let's build something sharp, reliable, and memorable.</h2>
                <p class="section-copy mx-auto mt-5 max-w-2xl">
                    If you have a project in mind, need website support, or want help with server-related work, send me a message and I will get back to you.
                </p>
            </div>

            <Transition name="fade">
                <div v-if="showSuccess" class="mx-auto mt-8 max-w-5xl rounded-[24px] border border-emerald-500/30 bg-emerald-500/10 px-5 py-4 text-center text-sm text-emerald-300">
                    Message sent successfully. I will get back to you soon.
                </div>
            </Transition>

            <div class="mt-10 grid gap-5 lg:grid-cols-[0.9fr_1.1fr]">
                <div class="space-y-5">
                    <div class="glass-panel rounded-[30px] p-6 sm:p-7">
                        <p class="text-xs uppercase tracking-[0.38em] text-white/40">Contact Details</p>

                        <div class="mt-5 space-y-4">
                            <article
                                v-for="info in contactInfo"
                                :key="info.label"
                                class="rounded-[22px] border border-white/10 bg-black/20 px-4 py-4 transition-all duration-300 hover:border-white/[0.16] hover:bg-black/[0.28]"
                            >
                                <p class="text-[11px] uppercase tracking-[0.36em] text-red-400/90">{{ info.label }}</p>
                                <p class="mt-2 break-words text-base text-white/[0.88]">{{ info.value }}</p>
                            </article>
                        </div>
                    </div>

                    <div class="glass-panel rounded-[30px] p-6 sm:p-7">
                        <p class="text-xs uppercase tracking-[0.38em] text-white/40">Work Style</p>
                        <div class="mt-5 grid gap-3 sm:grid-cols-2">
                            <div class="rounded-[22px] border border-white/10 bg-black/20 px-4 py-4">
                                <p class="text-sm font-semibold text-white">Fast Communication</p>
                                <p class="mt-2 text-sm leading-6 text-white/60">Clear updates and practical collaboration from start to finish.</p>
                            </div>
                            <div class="rounded-[22px] border border-white/10 bg-black/20 px-4 py-4">
                                <p class="text-sm font-semibold text-white">Responsive Builds</p>
                                <p class="mt-2 text-sm leading-6 text-white/60">Layouts designed to stay polished across screen sizes.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <form @submit.prevent="handleSubmit" class="glass-panel relative overflow-hidden rounded-[32px] p-6 sm:p-8 md:p-10">
                    <div class="absolute inset-x-0 top-0 h-32 bg-gradient-to-b from-red-500/10 to-transparent"></div>

                    <div class="relative z-10 space-y-5">
                        <div class="grid gap-5">
                            <div class="space-y-2">
                                <label class="ml-1 text-[10px] font-bold uppercase tracking-[0.36em] text-white/[0.42]">Full Name</label>
                                <input
                                    v-model="form.name"
                                    type="text"
                                    placeholder="John Doe"
                                    required
                                    class="w-full rounded-2xl border border-white/10 bg-black/20 px-4 py-3.5 text-sm text-white placeholder:text-white/[0.28] transition-all focus:border-red-400/[0.55] focus:outline-none focus:ring-2 focus:ring-red-400/[0.18] sm:px-5 sm:py-4 sm:text-base"
                                />
                            </div>

                            <div class="space-y-2">
                                <label class="ml-1 text-[10px] font-bold uppercase tracking-[0.36em] text-white/[0.42]">Email Address</label>
                                <input
                                    v-model="form.email"
                                    type="email"
                                    placeholder="john@example.com"
                                    required
                                    class="w-full rounded-2xl border border-white/10 bg-black/20 px-4 py-3.5 text-sm text-white placeholder:text-white/[0.28] transition-all focus:border-red-400/[0.55] focus:outline-none focus:ring-2 focus:ring-red-400/[0.18] sm:px-5 sm:py-4 sm:text-base"
                                />
                            </div>

                            <div class="space-y-2">
                                <label class="ml-1 text-[10px] font-bold uppercase tracking-[0.36em] text-white/[0.42]">Message</label>
                                <textarea
                                    v-model="form.message"
                                    rows="5"
                                    placeholder="Tell me about your project..."
                                    required
                                    class="min-h-[160px] w-full resize-none rounded-2xl border border-white/10 bg-black/20 px-4 py-3.5 text-sm text-white placeholder:text-white/[0.28] transition-all focus:border-red-400/[0.55] focus:outline-none focus:ring-2 focus:ring-red-400/[0.18] sm:px-5 sm:py-4 sm:text-base"
                                ></textarea>
                            </div>
                        </div>

                        <button
                            type="submit"
                            :disabled="isSubmitting"
                            class="inline-flex w-full items-center justify-center gap-3 rounded-2xl bg-gradient-to-r from-red-600 to-orange-500 px-6 py-3.5 text-sm font-semibold text-white shadow-[0_18px_45px_rgba(239,68,68,0.24)] transition-all duration-300 hover:-translate-y-1 hover:shadow-[0_22px_52px_rgba(249,115,22,0.28)] disabled:cursor-not-allowed disabled:opacity-60 sm:py-4 sm:text-base"
                        >
                            <span>{{ isSubmitting ? 'Sending...' : 'Send Message' }}</span>
                            <svg v-if="!isSubmitting" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                                <path d="m22 2-7 20-4-9-9-4Z" />
                                <path d="M22 2 11 13" />
                            </svg>
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import emailjs from '@emailjs/browser'

defineOptions({
    inheritAttrs: false
})

const isSubmitting = ref(false)
const showSuccess = ref(false)

const contactInfo = [
    { label: 'Email', value: 'vprogrammer11@gmail.com' },
    { label: 'Location', value: 'Surigao City, Philippines' },
    { label: 'Availability', value: 'Open for freelance and project work' }
]

const form = reactive({
    name: '',
    email: '',
    message: ''
})

const handleSubmit = async () => {
    isSubmitting.value = true

    const SERVICE_ID = 'service_t99aykp'
    const TEMPLATE_ID = 'template_0vsjeoh'
    const PUBLIC_KEY = 'IO2R6pfdCf4AijTba'

    const templateParams = {
        from_name: form.name,
        from_email: form.email,
        to_name: 'VProgrammer',
        message: form.message,
        reply_to: form.email
    }

    try {
        await emailjs.send(SERVICE_ID, TEMPLATE_ID, templateParams, PUBLIC_KEY)
        showSuccess.value = true
        form.name = ''
        form.email = ''
        form.message = ''
        setTimeout(() => {
            showSuccess.value = false
        }, 5000)
    } catch (error) {
        console.error('EMAILJS ERROR:', error)
        alert('Failed to send message.')
    } finally {
        isSubmitting.value = false
    }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: all 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(-8px);
}
</style>
