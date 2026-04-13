<template>
    <main class="relative min-h-screen overflow-hidden bg-[#070707] text-white selection:bg-red-500/30">
        <div class="ambient-orb left-[-8rem] top-20 h-72 w-72 bg-red-600/[0.14]"></div>
        <div class="ambient-orb right-[-10rem] top-[28rem] h-96 w-96 bg-orange-500/10 [animation-delay:1.8s]"></div>
        <div class="ambient-orb bottom-24 left-1/2 h-80 w-80 -translate-x-1/2 bg-white/[0.06] [animation-delay:3.2s]"></div>
        <div class="pointer-events-none absolute inset-0 grid-fade opacity-35"></div>

        <div class="relative mx-auto flex min-h-screen w-full max-w-[1480px]">
            <div class="mx-auto flex w-full flex-col px-3 pb-8 sm:px-5 lg:px-8">
                <header class="sticky top-0 z-50 pt-3 sm:pt-5">
                    <div class="section-shell rounded-[26px]">
                        <div class="relative flex min-h-[74px] items-center justify-between gap-4 px-4 py-3 sm:px-6">
                            <div class="absolute bottom-0 left-0 h-[2px] rounded-full bg-gradient-to-r from-red-500 via-orange-400 to-red-500 transition-all duration-150" :style="{ width: scrollPercent + '%' }"></div>

                            <div class="flex items-center gap-3">
                                <div class="flex h-10 w-10 items-center justify-center rounded-2xl border border-white/10 bg-white/[0.06] text-sm font-semibold tracking-[0.3em] text-white/80">
                                    VM
                                </div>
                                <div>
                                    <p class="text-sm font-medium text-white/[0.88]">Von Execquell Mauzar</p>
                                </div>
                            </div>

                            <nav class="hidden max-w-full items-center gap-2 overflow-x-auto whitespace-nowrap rounded-full border border-white/10 bg-black/20 px-2 py-2 text-[11px] font-medium text-white/[0.72] shadow-[inset_0_1px_0_rgba(255,255,255,0.08)] sm:gap-3 sm:text-sm md:flex">
                                <button
                                    v-for="item in navItems"
                                    :key="item.id"
                                    @click="scrollTo(item.id)"
                                    class="shrink-0 rounded-full px-3 py-2 transition-all duration-300 hover:bg-white/[0.06] hover:text-white sm:px-4"
                                    :class="activeSection === item.id ? 'bg-gradient-to-r from-red-600 to-orange-500 text-white shadow-[0_10px_30px_rgba(239,68,68,0.25)]' : ''"
                                >
                                    {{ item.name }}
                                </button>
                            </nav>

                            <button
                                type="button"
                                class="flex h-11 w-11 items-center justify-center rounded-2xl border border-white/10 bg-white/[0.04] text-white transition-all duration-300 hover:bg-white/[0.08] md:hidden"
                                :aria-expanded="mobileMenuOpen ? 'true' : 'false'"
                                aria-label="Toggle navigation menu"
                                @click="toggleMobileMenu"
                            >
                                <svg v-if="!mobileMenuOpen" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round">
                                    <path d="M4 7h16" />
                                    <path d="M4 12h16" />
                                    <path d="M4 17h16" />
                                </svg>
                                <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round">
                                    <path d="M18 6 6 18" />
                                    <path d="m6 6 12 12" />
                                </svg>
                            </button>
                        </div>

                        <Transition name="menu">
                            <div v-if="mobileMenuOpen" class="border-t border-white/8 px-4 pb-4 md:hidden">
                                <nav class="mt-3 grid gap-2 rounded-[22px] border border-white/10 bg-black/20 p-2">
                                    <button
                                        v-for="item in navItems"
                                        :key="item.id"
                                        @click="scrollTo(item.id, true)"
                                        class="rounded-[18px] px-4 py-3 text-left text-sm font-medium text-white/[0.78] transition-all duration-300 hover:bg-white/[0.06] hover:text-white"
                                        :class="activeSection === item.id ? 'bg-gradient-to-r from-red-600 to-orange-500 text-white shadow-[0_10px_30px_rgba(239,68,68,0.22)]' : ''"
                                    >
                                        {{ item.name }}
                                    </button>
                                </nav>
                            </div>
                        </Transition>
                    </div>
                </header>

                <div class="mt-4 space-y-4 sm:space-y-5">
                    <Home id="home" class="scroll-mt-[96px]" />

                    <div class="section-shell relative flex h-[74px] items-center justify-center overflow-hidden rounded-[28px] bg-[#121212]">
                        <div class="absolute inset-y-0 left-[-26px] flex w-28 -rotate-[25deg] items-center justify-center rounded-[24px] border border-white/[0.06] bg-white/[0.025] text-4xl font-semibold text-white/[0.08] sm:w-36 sm:text-5xl">
                            IT
                        </div>
                        <div class="absolute inset-y-0 right-[-26px] flex w-28 rotate-[25deg] items-center justify-center rounded-[24px] border border-white/[0.06] bg-white/[0.025] text-4xl font-semibold text-white/[0.08] sm:w-36 sm:text-5xl">
                            WEB
                        </div>
                        <p class="text-[11px] uppercase tracking-[0.45em] text-white/50 sm:text-xs">
                            Building fast interfaces and dependable systems
                        </p>
                    </div>

                    <About id="about" class="scroll-mt-[96px]" />
                    <Tools id="tools" class="scroll-mt-[96px]" />
                    <Certificates id="certificates" class="scroll-mt-[96px]" />
                    <Contact id="contacts" class="scroll-mt-[96px]" />
                </div>
            </div>
        </div>

        <Transition name="fade">
            <button
                v-show="showBackToTop"
                @click="scrollTo('home')"
                aria-label="Back to top"
                class="fixed bottom-4 right-4 z-[60] flex h-12 w-12 items-center justify-center rounded-full border border-white/10 bg-gradient-to-br from-red-600 to-orange-500 text-white shadow-[0_18px_45px_rgba(239,68,68,0.3)] transition-all duration-300 hover:scale-110 hover:shadow-[0_22px_50px_rgba(249,115,22,0.35)] active:scale-95 sm:bottom-8 sm:right-8 sm:h-14 sm:w-14"
            >
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <path d="m18 15-6-6-6 6" />
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
const mobileMenuOpen = ref(false)

const navItems = [
    { name: 'Home', id: 'home' },
    { name: 'About', id: 'about' },
    { name: 'Tools', id: 'tools' },
    { name: 'Certificates', id: 'certificates' },
    { name: 'Contact', id: 'contacts' }
]

const scrollTo = (id, closeMenu = false) => {
    const element = document.getElementById(id)
    if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
    if (closeMenu) {
        mobileMenuOpen.value = false
    }
}

const toggleMobileMenu = () => {
    mobileMenuOpen.value = !mobileMenuOpen.value
}

const handleScroll = () => {
    const scrollY = window.scrollY
    showBackToTop.value = scrollY > 420

    const documentHeight = document.documentElement.scrollHeight - window.innerHeight
    scrollPercent.value = documentHeight > 0 ? (scrollY / documentHeight) * 100 : 0

    navItems.forEach((item) => {
        const el = document.getElementById(item.id)
        if (el) {
            const offset = el.offsetTop - 180
            if (scrollY >= offset) {
                activeSection.value = item.id
            }
        }
    })
}

onMounted(() => {
    handleScroll()
    window.addEventListener('scroll', handleScroll, { passive: true })
    window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
    window.removeEventListener('resize', handleResize)
})

const handleResize = () => {
    if (window.innerWidth >= 768) {
        mobileMenuOpen.value = false
    }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: all 0.35s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
    transform: translateY(16px) scale(0.92);
}

.menu-enter-active,
.menu-leave-active {
    transition: all 0.25s ease;
}

.menu-enter-from,
.menu-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}
</style>
