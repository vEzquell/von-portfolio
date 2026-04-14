<template>
  <section class="section-shell relative min-h-[calc(100vh-110px)] rounded-[34px] px-4 py-8 sm:px-6 md:px-8 lg:px-10">
    <div class="ambient-orb left-[-4rem] top-10 h-44 w-44 bg-red-600/20"></div>
    <div class="ambient-orb right-[-3rem] top-20 h-56 w-56 bg-orange-400/[0.14] [animation-delay:1.4s]"></div>
    <div class="pointer-events-none absolute inset-0 bg-[radial-gradient(circle_at_top_right,rgba(255,255,255,0.12),transparent_28%),linear-gradient(135deg,rgba(255,255,255,0.03),transparent_42%)]"></div>

    <div class="relative z-10 grid min-h-[calc(100vh-174px)] items-center gap-10 md:grid-cols-[1.15fr_0.85fr]">
      <div class="order-2 space-y-8 text-center md:order-1 md:text-left">
        <div class="section-kicker mx-auto md:mx-0">
          <span class="h-2 w-2 rounded-full bg-red-500 shadow-[0_0_18px_rgba(239,68,68,0.7)]"></span>
          Full-Stack Web Developer
        </div>

        <div class="space-y-5">
          <p class="text-xs uppercase tracking-[0.5em] text-white/40">Surigao City, Philippines</p>
          <h1 class="max-w-3xl text-4xl font-semibold leading-tight text-white sm:text-5xl lg:text-6xl xl:text-7xl">
            Fast and
            <span class="bg-gradient-to-r from-red-400 via-orange-300 to-white bg-clip-text text-transparent">intentional</span>
            web experiences.
          </h1>
          <p class="mx-auto max-w-2xl text-sm leading-7 text-white/[0.68] sm:text-base md:mx-0 lg:text-lg">
            I design and build polished websites, admin systems, and server-backed products with a clean visual feel, thoughtful interactions, and reliable performance.
          </p>
        </div>

        <div class="flex flex-col items-stretch gap-3 sm:flex-row sm:justify-center md:justify-start">
          <button
            @click="scrollToSection('tools')"
            class="group inline-flex items-center justify-center gap-3 rounded-2xl bg-gradient-to-r from-red-600 to-orange-500 px-6 py-3.5 text-sm font-semibold text-white shadow-[0_18px_45px_rgba(239,68,68,0.28)] transition-all duration-300 hover:-translate-y-1 hover:shadow-[0_22px_50px_rgba(249,115,22,0.32)] sm:px-7 sm:text-base"
          >
            View My Work
            <svg xmlns="http://www.w3.org/2000/svg" class="transition-transform duration-300 group-hover:translate-x-1" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M5 12h14" />
              <path d="m12 5 7 7-7 7" />
            </svg>
          </button>

          <a
            href="/resume/Von Resume.pdf"
            download="Von-Resume.pdf"
            class="inline-flex items-center justify-center gap-3 rounded-2xl border border-orange-400/30 bg-orange-500/10 px-6 py-3.5 text-sm font-medium text-white transition-all duration-300 hover:-translate-y-1 hover:border-orange-300/50 hover:bg-orange-500/16 sm:px-7 sm:text-base"
          >
            Download Resume
            <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 3v12" />
              <path d="m7 10 5 5 5-5" />
              <path d="M5 21h14" />
            </svg>
          </a>

          <button
            @click="scrollToSection('contacts')"
            class="inline-flex items-center justify-center gap-3 rounded-2xl border border-white/[0.12] bg-white/[0.03] px-6 py-3.5 text-sm font-medium text-white/90 transition-all duration-300 hover:-translate-y-1 hover:border-white/20 hover:bg-white/[0.06] sm:px-7 sm:text-base"
          >
            Get In Touch
          </button>
        </div>

        <div class="grid gap-3 pt-2 sm:grid-cols-3">
          <div v-for="stat in stats" :key="stat.label" class="glass-panel rounded-[22px] px-4 py-4 text-left">
            <p class="text-2xl font-semibold text-white">{{ stat.value }}</p>
            <p class="mt-1 text-xs uppercase tracking-[0.3em] text-white/[0.45]">{{ stat.label }}</p>
          </div>
        </div>
      </div>

      <div class="order-1 flex justify-center md:order-2 md:justify-end">
        <div class="relative w-full max-w-[460px]">
          <div class="absolute inset-0 rounded-[34px] bg-gradient-to-br from-red-500/[0.24] via-transparent to-orange-400/[0.18] blur-2xl"></div>
          <div class="glass-panel relative overflow-hidden rounded-[34px] border-white/[0.12] p-4 sm:p-5">
            <div class="absolute inset-0 bg-[linear-gradient(140deg,rgba(255,255,255,0.12),transparent_35%,transparent_70%,rgba(255,255,255,0.08))]"></div>
            <div class="relative overflow-hidden rounded-[28px] border border-white/10 bg-[#0d0d0d]">
              <div class="absolute inset-x-0 top-0 h-24 bg-gradient-to-b from-red-500/[0.16] to-transparent"></div>
              <img
                src="/images/me.png"
                alt="Von portrait"
                class="relative z-10 aspect-[4/4.8] w-full object-cover transition-transform duration-700 hover:scale-[1.03]"
              />
            </div>

            <div class="relative mt-4 grid gap-3 sm:grid-cols-2">
              <div class="rounded-[22px] border border-white/10 bg-black/[0.22] px-4 py-4">
                <p class="text-xs uppercase tracking-[0.3em] text-white/[0.45]">Focus</p>
                <p class="mt-2 text-sm text-white/80">Frontend polish, backend structure, deployment stability.</p>
              </div>
              <div class="rounded-[22px] border border-white/10 bg-black/[0.22] px-4 py-4">
                <p class="text-xs uppercase tracking-[0.3em] text-white/[0.45]">Style</p>
                <p class="mt-2 text-sm text-white/80">Dark UI, rich contrast, subtle motion, clean hierarchy.</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stats = [
  { value: '3+', label: 'Core Services' },
  { value: '8', label: 'Main Tools' },
  { value: '24/7', label: 'Build Mindset' }
]

const scrollToSection = (id) => {
  const section = document.getElementById(id)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>
