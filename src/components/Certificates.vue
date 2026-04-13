<template>
    <div class="w-full h-auto bg-[#1A1818] py-10 sm:py-14 px-4 sm:px-6 flex flex-col items-center justify-center font-sans overflow-hidden">

        <div class="inline-flex items-center gap-3 bg-white/5 backdrop-blur-md border border-white/10 rounded-full px-4 sm:px-8 py-3 mb-10 sm:mb-16 shadow-xl text-center">
            <div class="w-2 h-2 bg-red-500 rounded-full animate-ping"></div>
            <span class="text-[10px] sm:text-xs font-bold tracking-[2px] sm:tracking-[4px] uppercase text-gray-300">Credentials & Certifications</span>
        </div>

        <div class="w-full max-w-5xl relative group">
            <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[280px] h-[280px] sm:w-[500px] sm:h-[500px] bg-red-500/10 rounded-full blur-[90px] sm:blur-[120px] pointer-events-none"></div>

            <div class="relative flex items-center justify-between gap-4 sm:gap-8">

                <button @click="prevSlide" class="hidden md:flex z-10 w-14 h-14 items-center justify-center rounded-full bg-white/5 border border-white/10 text-white hover:bg-red-500 hover:border-red-500 transition-all duration-300 group-hover:opacity-100 opacity-40">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>
                </button>

                <div 
                    class="relative w-full h-full max-w-3xl aspect-[16/11] sm:aspect-[16/10] overflow-hidden rounded-[28px] sm:rounded-[40px] border border-white/10 bg-[#1A1818]/80 backdrop-blur-sm shadow-2xl"
                    @mouseenter="stopAutoSlide"
                    @mouseleave="startAutoSlide"
                >
                    <div 
                        v-for="(cert, index) in certificates" 
                        :key="index"
                        class="absolute inset-0 p-4 sm:p-8 transition-all duration-1000 ease-in-out flex flex-col items-center"
                        :class="[
                            currentIndex === index ? 'opacity-100 translate-x-0 scale-100' : 'opacity-0 translate-x-12 scale-95 pointer-events-none'
                        ]"
                    >
                        <!-- Image Container - This is the key fix -->
                        <div class="relative flex-1 w-full flex items-center justify-center overflow-hidden">
                            <img 
                                :src="cert.icon" 
                                :alt="cert.name" 
                                class="max-h-full max-w-full w-auto h-auto object-contain 
                                    transition-transform duration-700 hover:scale-105 select-none 
                                    drop-shadow-[0_20px_50px_rgba(0,0,0,0.5)]"
                            />
                        </div>

                        <!-- Text Section -->
                        <div class="mt-5 sm:mt-8 text-center">
                            <p class="text-red-500 text-[10px] sm:text-xs font-bold tracking-[2px] uppercase mb-2">Verified Achievement</p>
                            <h3 class="text-lg sm:text-2xl md:text-3xl font-bold text-white tracking-tight italic">
                                {{ cert.name }}
                            </h3>
                        </div>
                    </div>
                </div>

                <button @click="nextSlide" class="hidden md:flex z-10 w-14 h-14 items-center justify-center rounded-full bg-white/5 border border-white/10 text-white hover:bg-red-500 hover:border-red-500 transition-all duration-300 group-hover:opacity-100 opacity-40">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
                </button>
            </div>

            <div class="flex md:hidden justify-center gap-3 mt-6">
                <button @click="prevSlide" class="w-11 h-11 flex items-center justify-center rounded-full bg-white/5 border border-white/10 text-white hover:bg-red-500 hover:border-red-500 transition-all duration-300">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>
                </button>
                <button @click="nextSlide" class="w-11 h-11 flex items-center justify-center rounded-full bg-white/5 border border-white/10 text-white hover:bg-red-500 hover:border-red-500 transition-all duration-300">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>
                </button>
            </div>

            <div class="flex justify-center gap-3 mt-8 sm:mt-12">
                <button
                    v-for="(cert, index) in certificates"
                    :key="index"
                    @click="goToSlide(index)"
                    class="relative h-1.5 transition-all duration-500 rounded-full"
                    :class="currentIndex === index ? 'w-12 bg-red-500' : 'w-3 bg-white/20 hover:bg-white/40'"
                >
                    <span v-if="currentIndex === index" class="absolute inset-0 bg-red-400 blur-sm rounded-full animate-pulse"></span>
                </button>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { ref, onMounted, onUnmounted } from 'vue'

    const certificates = ref([
        { name: 'WHM Administration', icon: '/images/WHM Administration Certificate.png' },
        { name: 'cPanel Professional', icon: '/images/cPanel Professional Certificate.png' },
        { name: 'cPanel & WHM System Administrator I', icon: '/images/cPanel & WHM System Administrator Certificate.png' },
        { name: 'cPanel & WHM System Administrator  II', icon: '/images/cPanel & WHM System Administrator Certificate 2.png' }
    ])

    const currentIndex = ref(0)
    let interval = null

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
    // Reduced to 8 seconds - 60 seconds is too long for a user to wait!
    interval = setInterval(nextSlide, 8000)
    }

    const stopAutoSlide = () => {
    if (interval) clearInterval(interval)
    }

    onMounted(startAutoSlide)
    onUnmounted(stopAutoSlide)
</script>

<style scoped>
    /* Optional: smooth easing for the slide transitions */
    .transition-all {
        transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    }
</style>
