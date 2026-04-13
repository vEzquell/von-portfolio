<template>
  <section class="section-shell relative rounded-[34px] px-4 py-12 sm:px-6 sm:py-14 md:px-8">
    <div class="ambient-orb right-[-5rem] top-[-3rem] h-40 w-40 bg-red-500/[0.16]"></div>

    <div class="relative z-10">
      <div class="mx-auto max-w-3xl text-center">
        <div class="section-kicker mx-auto">
          <span class="h-2 w-2 rounded-full bg-orange-400"></span>
          About Me
        </div>
        <h2 class="section-title mt-5">Building useful systems with a polished visual edge.</h2>
        <p class="section-copy mx-auto mt-5 max-w-2xl">
          I focus on interfaces that feel premium but stay practical underneath. My work blends responsive frontend design, structured backend thinking, and a strong preference for clean, maintainable implementation.
        </p>
      </div>

      <div class="mt-10 grid gap-5 lg:grid-cols-[1.15fr_0.85fr]">
        <div class="glass-panel rounded-[30px] p-6 sm:p-8">
          <p class="text-xs uppercase tracking-[0.4em] text-white/[0.45]">Approach</p>
          <p class="mt-4 text-base leading-8 text-white/[0.76]">
            I enjoy taking rough ideas and turning them into focused products with clear hierarchy, elegant dark-mode styling, and interactions that feel smooth without becoming distracting. Whether it is a portfolio, admin interface, or business tool, I care about both the user experience and the engineering underneath it.
          </p>

          <div class="mt-8 grid gap-4 sm:grid-cols-3">
            <div v-for="pillar in pillars" :key="pillar.title" class="rounded-[22px] border border-white/10 bg-black/[0.22] px-4 py-4">
              <p class="text-sm font-semibold text-white">{{ pillar.title }}</p>
              <p class="mt-2 text-sm leading-6 text-white/[0.58]">{{ pillar.copy }}</p>
            </div>
          </div>
        </div>

        <div class="grid gap-5">
          <article v-for="service in services" :key="service.title" class="glass-panel group rounded-[30px] p-6 transition-all duration-300 hover:-translate-y-1 hover:border-white/[0.16]">
            <div class="flex items-start gap-4">
              <div class="flex h-14 w-14 shrink-0 items-center justify-center rounded-2xl bg-gradient-to-br from-red-600/[0.18] to-orange-400/[0.16] ring-1 ring-white/10">
                <img :src="service.icon" :alt="service.title" class="h-8 w-8 object-contain" />
              </div>
              <div>
                <p class="text-xs uppercase tracking-[0.35em] text-white/40">{{ service.kicker }}</p>
                <h3 class="mt-2 text-2xl font-semibold text-white">{{ service.title }}</h3>
                <p class="mt-3 text-sm leading-7 text-white/[0.66]">{{ service.copy }}</p>
              </div>
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const pillars = [
  { title: 'Visual Clarity', copy: 'Readable layouts, strong contrast, and intentional spacing.' },
  { title: 'Responsive UX', copy: 'Interfaces that hold up cleanly from phone to desktop.' },
  { title: 'Reliable Builds', copy: 'Practical code that is easier to maintain and extend.' }
]

const services = [
  {
    kicker: 'Service 01',
    title: 'Development',
    copy: 'From initial concept to launch, I build websites and application interfaces that are fast, flexible, and aligned with your goals.',
    icon: '/images/development.png'
  },
  {
    kicker: 'Service 02',
    title: 'Maintenance',
    copy: 'I help improve existing projects with fixes, UI refinement, cleanup, and ongoing support so your product stays dependable.',
    icon: '/images/maintenance.png'
  }
]
</script>
