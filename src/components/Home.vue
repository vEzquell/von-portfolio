<template>
  <div class="relative w-full min-h-screen md:min-h-[600px] overflow-hidden bg-[#0a0a0a] flex items-center py-16 sm:py-20">
    <!-- Background gradient overlay -->
    <div class="absolute inset-0 bg-gradient-to-br from-violet-950/40 via-black to-black z-0"></div>

    <div class="w-full max-w-7xl mx-auto px-4 sm:px-6 md:px-12 grid grid-cols-1 md:grid-cols-2 gap-10 md:gap-12 items-center h-full relative z-10">
      <!-- Left: Image -->
      <div class="flex justify-center md:justify-end">
        <div class="relative group">
          <!-- Glow effect -->
          
          <img 
            src="/images/me.png" 
            alt="Von" 
            class="w-[220px] sm:w-[280px] md:w-[380px] h-auto rounded-3xl shadow-2xl object-cover transition-transform duration-500 group-hover:scale-105 border border-white/10"
          />
        </div>
      </div>

      <!-- Right: Text Content -->
      <div class="flex flex-col justify-center md:items-start items-center text-center md:text-left">
        <div class="backdrop-blur-xl bg-white/5 border border-white/10 rounded-3xl p-6 sm:p-8 md:p-10 shadow-2xl w-full max-w-md">
          <h1 class="text-4xl sm:text-5xl md:text-6xl font-bold text-white tracking-tighter mb-3">
            Hi, I'm <span class="bg-gradient-to-r from-violet-400 to-fuchsia-400 bg-clip-text text-transparent">Von</span>
          </h1>
          
          <div class="space-y-1 mb-6 sm:mb-8">
            <h2 class="text-xl sm:text-2xl md:text-3xl font-medium text-white/90">Web Developer</h2>
            <h2 class="text-xl sm:text-2xl md:text-3xl font-medium text-white/90">Full-Stack Engineer</h2>
          </div>

          <!-- Optional subtitle / tagline -->
          <p class="text-white/70 text-base sm:text-lg leading-relaxed">
            Crafting beautiful, high-performance web experiences with clean code and modern design.
          </p>

          <!-- Call to action buttons -->
          <div class="flex flex-col sm:flex-row gap-3 sm:gap-4 mt-8 sm:mt-10">
            <button 
              class="w-full sm:w-auto px-6 sm:px-8 py-3.5 sm:py-4 bg-white text-black text-sm sm:text-base font-semibold rounded-2xl hover:bg-white/90 transition-all active:scale-95 flex items-center justify-center gap-2"
            >
              View My Work
              <span class="text-xl">→</span>
            </button>
            
            <button 
              class="w-full sm:w-auto px-6 sm:px-8 py-3.5 sm:py-4 border border-white/30 hover:border-white/60 text-white text-sm sm:text-base font-medium rounded-2xl transition-all active:scale-95"
            >
              Get In Touch
            </button>
          </div>
        </div>

        <!-- Subtle social links or scroll indicator (optional) -->
        <div class="mt-8 sm:mt-12 flex gap-6 text-white/40">
          <!-- Add your social icons here if you want -->
        </div>
      </div>
    </div>

    <!-- Optional decorative element -->
    <div class="absolute bottom-10 right-10 hidden lg:block text-[120px] font-black text-white/5 select-none pointer-events-none">
      VON
    </div>
  </div>
</template>

<script setup>
// You can add any interactivity here later (e.g. scroll animations with IntersectionObserver)
</script>
