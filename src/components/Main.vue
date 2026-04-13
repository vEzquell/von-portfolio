<template>
    <main class="min-h-screen bg-[#202020] flex justify-center scroll-smooth selection:bg-red-500/30">
        <div class="flex flex-col w-full xl:w-[70%] 2xl:w-[50%]">
            
            <div class="w-full min-h-[70px] bg-[#1A1818]/90 sticky top-0 backdrop-blur-md border-b border-white/10 flex items-center justify-center md:justify-end px-3 sm:px-4 md:px-8 py-3 z-50">
                <div class="absolute bottom-0 left-0 h-[2px] bg-red-600 transition-all duration-150" :style="{ width: scrollPercent + '%' }"></div>

                <nav class="flex items-center gap-3 sm:gap-4 md:gap-8 text-[11px] sm:text-sm font-medium text-white/90 overflow-x-auto max-w-full whitespace-nowrap">
                    <button 
                        v-for="item in navItems" 
                        :key="item.id"
                        @click="scrollTo(item.id)" 
                        class="relative py-2 px-1 transition-colors hover:text-white group shrink-0"
                        :class="{ 'text-red-500': activeSection === item.id }"
                    >
                        {{ item.name }}
                        <span 
                            class="absolute bottom-0 left-0 h-[2px] bg-red-500 transition-all duration-300"
                            :class="activeSection === item.id ? 'w-full' : 'w-0 group-hover:w-full'"
                        ></span>
                    </button>
                </nav>
            </div>

            <Home id="home" class="scroll-mt-[70px]" />
            
            <div class="w-full h-[64px] sm:h-[80px] bg-[#1D1D1D] relative overflow-hidden flex items-center justify-center">
                 <div class="absolute left-[-24px] sm:left-[-20px] -rotate-[30deg] w-[90px] h-[84px] sm:w-[120px] sm:h-[110px] border-[5px] sm:border-[7px] border-black/40 flex items-center justify-center rounded-[18px] sm:rounded-[20px] pointer-events-none">
                    <span class="text-black/40 text-[2.75em] sm:text-[4em] font-bold select-none">IT</span>
                </div>
                <div class="absolute right-[-24px] sm:right-[-20px] -rotate-[30deg] w-[90px] h-[84px] sm:w-[120px] sm:h-[110px] border-[5px] sm:border-[7px] border-black/40 flex items-center justify-center rounded-[18px] sm:rounded-[20px] pointer-events-none">
                    <span class="text-black/40 text-[2.75em] sm:text-[4em] font-bold select-none">IT</span>
                </div>
            </div>

            <About id="about" class="scroll-mt-[70px]" />
            <Tools id="tools" class="scroll-mt-[70px]" />
            <Certificates id="certificates" class="scroll-mt-[70px]" />
            <Contact id="contacts" class="scroll-mt-[70px]" />
        </div>

        <Transition name="fade">
            <button 
                v-show="showBackToTop" 
                @click="scrollTo('home')"
                aria-label="Back to top"
                class="fixed bottom-4 right-4 sm:bottom-8 sm:right-8 z-[60] w-12 h-12 sm:w-14 sm:h-14 bg-red-600 text-white rounded-full shadow-[0_0_20px_rgba(220,38,38,0.4)] flex items-center justify-center hover:bg-red-500 transition-all duration-300 hover:scale-110 active:scale-95 group"
            >
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" class="group-hover:-translate-y-1 transition-transform">
                    <path d="m18 15-6-6-6 6"/>
                </svg>
            </button>
        </Transition>
    </main>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import Home from './Home.vue'
import About from './About.vue'
import Tools from './Tools.vue'
import Certificates from './Certificates.vue'
import Contact from './Contact.vue'

const showBackToTop = ref(false)
const scrollPercent = ref(0)
const activeSection = ref('home')

const navItems = [
    { name: 'Home', id: 'home' },
    { name: 'About', id: 'about' },
    { name: 'Tools', id: 'tools' },
    { name: 'Certificates', id: 'certificates' },
    { name: 'Contact', id: 'contacts' }
]

const scrollTo = (id) => {
    const element = document.getElementById(id)
    if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
    }
}

const handleScroll = () => {
    const scrollY = window.scrollY
    showBackToTop.value = scrollY > 400

    // Calculate reading progress percentage
    const windowHeight = document.documentElement.scrollHeight - window.innerHeight
    scrollPercent.value = (scrollY / windowHeight) * 100

    // Update active section based on scroll position
    navItems.forEach(item => {
        const el = document.getElementById(item.id)
        if (el) {
            const offset = el.offsetTop - 100
            if (scrollY >= offset) {
                activeSection.value = item.id
            }
        }
    })
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(30px) scale(0.5);
}
</style>
