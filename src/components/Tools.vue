<template>
    <section class="section-shell relative rounded-[34px] px-4 py-12 sm:px-6 sm:py-14 md:px-8">
        <div class="ambient-orb left-[-4rem] top-12 h-44 w-44 bg-orange-500/[0.12]"></div>

        <div class="relative z-10">
            <div class="mx-auto max-w-3xl text-center">
                <div class="section-kicker mx-auto">
                    <span class="h-2 w-2 rounded-full bg-red-500"></span>
                    Tools and Technologies
                </div>
                <h2 class="section-title mt-5">A stack focused on modern interfaces and dependable builds.</h2>
                <p class="section-copy mx-auto mt-5 max-w-2xl">
                    These are the tools I reach for most when building frontend experiences, backend features, and production-ready web projects.
                </p>
            </div>

            <div class="mt-10 grid grid-cols-2 gap-4 sm:grid-cols-3 lg:grid-cols-4">
                <article
                    v-for="tool in tools"
                    :key="tool.name"
                    class="glass-panel group relative overflow-hidden rounded-[28px] p-4 transition-all duration-300 hover:-translate-y-1 hover:border-white/[0.18]"
                >
                    <div class="absolute inset-x-0 top-0 h-20 bg-gradient-to-b from-white/[0.07] to-transparent opacity-0 transition-opacity duration-300 group-hover:opacity-100"></div>
                    <div class="relative flex flex-col items-start gap-4">
                        <div class="flex h-16 w-16 items-center justify-center rounded-2xl border border-white/10 bg-[#0f0f0f] transition-transform duration-300 group-hover:scale-105">
                            <img
                                :src="tool.icon"
                                :alt="tool.name"
                                class="h-10 w-10 object-contain"
                            />
                        </div>

                        <div>
                            <p class="text-lg font-semibold italic tracking-tight text-white">{{ tool.name }}</p>
                            <p class="mt-1 text-xs uppercase tracking-[0.28em] text-white/40">{{ tool.type }}</p>
                        </div>
                    </div>
                </article>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const tools = ref([
    { name: 'Vue', icon: '/images/vue.png', type: 'Frontend' },
    { name: 'React', icon: '/images/react.png', type: 'Frontend' },
    { name: 'JavaScript', icon: '/images/js.png', type: 'Language' },
    { name: 'HTML', icon: '/images/html.png', type: 'Markup' },
    { name: 'CSS', icon: '/images/css.png', type: 'Styling' },
    { name: 'PHP', icon: '/images/php.png', type: 'Backend' },
    { name: 'Laravel', icon: '/images/laravel.png', type: 'Framework' },
    { name: 'MySQL', icon: '/images/mysql.png', type: 'Database' }
])
</script>
