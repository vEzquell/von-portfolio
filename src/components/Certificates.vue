<template>
    <section class="section-shell relative rounded-[34px] px-4 py-12 sm:px-6 sm:py-14 md:px-8">
        <div class="ambient-orb right-[-4rem] top-10 h-44 w-44 bg-red-500/[0.16]"></div>

        <div class="relative z-10">
            <div class="mx-auto max-w-3xl text-center">
                <div class="section-kicker mx-auto">
                    <span class="h-2 w-2 rounded-full bg-orange-400"></span>
                    Certificates
                </div>
                <p class="section-copy mx-auto mt-5 max-w-2xl">
                    This is the Certificates that I have earned through my professional experience.
                </p>
            </div>

            <div class="mt-10">
                <div class="relative mx-auto flex max-w-5xl items-center gap-4">
                    <button
                        @click="prevSlide"
                        class="hidden h-14 w-14 shrink-0 items-center justify-center rounded-full border border-white/10 bg-white/[0.04] text-white/80 transition-all duration-300 hover:border-white/20 hover:bg-white/[0.08] md:flex"
                    >
                        <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="m15 18-6-6 6-6" />
                        </svg>
                    </button>

                    <div
                        class="glass-panel relative w-full overflow-hidden rounded-[32px] p-4 sm:p-5"
                        @mouseenter="stopAutoSlide"
                        @mouseleave="startAutoSlide"
                    >
                        <div class="absolute inset-0 bg-[radial-gradient(circle_at_top,rgba(239,68,68,0.12),transparent_34%)]"></div>

                        <div
                            v-for="(cert, index) in certificates"
                            :key="index"
                            class="absolute inset-0 p-4 transition-all duration-700 ease-out sm:p-5"
                            :class="currentIndex === index ? 'opacity-100 translate-x-0' : 'pointer-events-none opacity-0 translate-x-10'"
                        >
                            <div class="grid h-full gap-5 md:grid-cols-[1.1fr_0.9fr]">
                                <button
                                    class="group relative overflow-hidden rounded-[28px] border border-white/10 bg-[#0f0f0f] text-left"
                                    @click="openImage(cert.icon)"
                                >
                                    <div class="absolute inset-0 bg-gradient-to-br from-red-500/[0.14] via-transparent to-orange-400/[0.12]"></div>
                                    <img
                                        :src="cert.icon"
                                        :alt="cert.name"
                                        class="relative z-10 h-full w-full object-contain p-4 transition-transform duration-500 group-hover:scale-[1.02] sm:p-6"
                                    />
                                </button>

                                <div class="flex flex-col justify-center rounded-[28px] border border-white/10 bg-black/[0.22] p-5 sm:p-7">
                                    <p class="text-xs uppercase tracking-[0.38em] text-white/40">Verified Achievement</p>
                                    <h3 class="mt-4 text-2xl font-semibold text-white sm:text-3xl">{{ cert.name }}</h3>
                                    <p class="mt-4 text-sm leading-7 text-white/[0.66]">
                                        Professional training that supports backend administration, hosting operations, and practical deployment work.
                                    </p>

                                    <div class="mt-6 flex flex-col gap-3 sm:flex-row">
                                        <button
                                            @click="openImage(cert.icon)"
                                            class="inline-flex items-center justify-center rounded-2xl bg-gradient-to-r from-red-600 to-orange-500 px-5 py-3 text-sm font-semibold text-white transition-transform duration-300 hover:-translate-y-1"
                                        >
                                            Open Certificate
                                        </button>
                                        <div class="inline-flex items-center justify-center rounded-2xl border border-white/10 px-5 py-3 text-sm text-white/[0.65]">
                                            {{ index + 1 }} / {{ certificates.length }}
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="pointer-events-none h-[430px] sm:h-[480px]"></div>
                    </div>

                    <button
                        @click="nextSlide"
                        class="hidden h-14 w-14 shrink-0 items-center justify-center rounded-full border border-white/10 bg-white/[0.04] text-white/80 transition-all duration-300 hover:border-white/20 hover:bg-white/[0.08] md:flex"
                    >
                        <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="m9 18 6-6-6-6" />
                        </svg>
                    </button>
                </div>

                <div class="mt-5 flex justify-center gap-3 md:hidden">
                    <button @click="prevSlide" class="flex h-11 w-11 items-center justify-center rounded-full border border-white/10 bg-white/[0.04] text-white/75">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="m15 18-6-6 6-6" />
                        </svg>
                    </button>
                    <button @click="nextSlide" class="flex h-11 w-11 items-center justify-center rounded-full border border-white/10 bg-white/[0.04] text-white/75">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="m9 18 6-6-6-6" />
                        </svg>
                    </button>
                </div>

                <div class="mt-6 flex justify-center gap-3">
                    <button
                        v-for="(cert, index) in certificates"
                        :key="index"
                        @click="goToSlide(index)"
                        class="h-2 rounded-full transition-all duration-300"
                        :class="currentIndex === index ? 'w-12 bg-gradient-to-r from-red-500 to-orange-400' : 'w-3 bg-white/20 hover:bg-white/40'"
                    ></button>
                </div>
            </div>
        </div>

        <Transition name="viewer">
            <div
                v-if="showImage"
                class="fixed inset-0 z-[70] flex items-center justify-center bg-black/90 p-4 backdrop-blur-md"
                @click="closeImage"
            >
                <div class="relative max-h-full max-w-6xl">
                    <img
                        :src="selectedImage"
                        alt="Certificate preview"
                        class="max-h-[88vh] rounded-[24px] border border-white/10 object-contain"
                        @click.stop
                    />
                    <button
                        class="absolute right-4 top-4 flex h-10 w-10 items-center justify-center rounded-full border border-white/[0.12] bg-black/[0.38] text-white/90"
                        @click.stop="closeImage"
                    >
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M18 6 6 18" />
                            <path d="m6 6 12 12" />
                        </svg>
                    </button>
                </div>
            </div>
        </Transition>
    </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const certificates = ref([
    { name: 'WHM Administration', icon: '/images/WHM Administration Certificate.png' },
    { name: 'cPanel Professional', icon: '/images/cPanel Professional Certificate.png' },
    { name: 'cPanel & WHM System Administrator I', icon: '/images/cPanel & WHM System Administrator Certificate.png' },
    { name: 'cPanel & WHM System Administrator II', icon: '/images/cPanel & WHM System Administrator Certificate 2.png' }
])

const currentIndex = ref(0)
const showImage = ref(false)
const selectedImage = ref('')
let interval = null

const openImage = (img) => {
    selectedImage.value = img
    showImage.value = true
}

const closeImage = () => {
    showImage.value = false
}

const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % certificates.value.length
}

const prevSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + certificates.value.length) % certificates.value.length
}

const goToSlide = (index) => {
    currentIndex.value = index
}

const startAutoSlide = () => {
    stopAutoSlide()
    interval = setInterval(nextSlide, 7000)
}

const stopAutoSlide = () => {
    if (interval) clearInterval(interval)
}

onMounted(startAutoSlide)
onUnmounted(stopAutoSlide)
</script>

<style scoped>
.viewer-enter-active,
.viewer-leave-active {
    transition: opacity 0.3s ease;
}

.viewer-enter-from,
.viewer-leave-to {
    opacity: 0;
}
</style>
