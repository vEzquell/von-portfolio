<template>
    <div class="w-full h-auto bg-[#1A1818] py-10 sm:py-14 px-4 sm:px-6 flex flex-col items-center">

        <!-- Title Badge -->
        <div class="inline-flex items-center gap-3 bg-[#2E2A2A] border border-white/10 rounded-3xl px-5 sm:px-10 py-3 sm:py-4 mb-10 sm:mb-16 text-center">
            <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
            <span class="text-sm sm:text-xl font-medium tracking-[2px] sm:tracking-[3px] uppercase">TOOLS &amp; TECHNOLOGIES</span>
        </div>

        <!-- Tools Grid -->
        <div class="w-full max-w-5xl grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4 sm:gap-6 md:gap-8">
            <div 
                v-for="tool in tools" 
                    :key="tool.name"
                    class="group flex flex-col items-center gap-3 sm:gap-4 bg-[#2E2A2A] border border-white/10 hover:border-red-500/50 rounded-3xl p-4 sm:p-6 md:p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-2xl hover:shadow-red-500/10"
                >
                <div class="w-16 h-16 sm:w-20 sm:h-20 flex items-center justify-center bg-[#1A1818] rounded-2xl transition-transform duration-500 group-hover:scale-110">
                    <img 
                        :src="tool.icon" 
                        :alt="tool.name" 
                        class="w-10 h-10 sm:w-14 sm:h-14 object-contain filter brightness-90 group-hover:brightness-100 transition-all"
                    />
                </div>

                <span class="text-white font-medium text-sm sm:text-lg mt-1 sm:mt-2 tracking-tight italic text-center break-words">
                    {{ tool.name }}
                </span>
            </div>
        </div>

    </div>
</template>

<script setup>
    import { ref } from 'vue'

    const tools = ref([
        { name: 'Vue', icon: '/images/vue.png' },
        { name: 'React', icon: '/images/react.png' },
        { name: 'JavaScript', icon: '/images/js.png' },
        { name: 'HTML', icon: '/images/html.png' },
        { name: 'CSS', icon: '/images/css.png' },
        { name: 'PHP', icon: '/images/php.png' },
        { name: 'Laravel', icon: '/images/laravel.png' },
        { name: 'MySQL', icon: '/images/mysql.png' }
    ])
</script>
