<template>
  <div class="w-full h-auto bg-[#1A1818] text-white py-10 sm:py-14 px-4 sm:px-6 flex flex-col items-center">
    
    <!-- Title Badge -->
    <div class="inline-flex items-center gap-3 bg-[#2E2A2A] border border-white/10 rounded-3xl px-5 sm:px-8 py-3 mb-10 sm:mb-12">
      <div class="w-3 h-3 bg-red-500 rounded-full animate-pulse"></div>
      <span class="text-sm sm:text-lg font-medium tracking-[0.2em] sm:tracking-widest">ABOUT ME</span>
    </div>

    <!-- Main Description -->
    <div class="max-w-3xl text-center">
      <p class="text-base sm:text-lg leading-relaxed text-white/80">
        I am a passionate web developer who loves crafting functional, beautiful, 
        and user-friendly web applications. I specialize in building efficient backend systems 
        and responsive interfaces while constantly learning new technologies to elevate my craft.
      </p>
    </div>

    <!-- Services Section -->
    <div class="mt-12 sm:mt-20 w-full max-w-4xl grid grid-cols-1 md:grid-cols-2 gap-6 sm:gap-10">
      
      <!-- Development Card -->
      <div class="group bg-[#2E2A2A] border border-white/5 hover:border-white/20 rounded-3xl p-6 sm:p-10 transition-all duration-500 hover:-translate-y-2">
        <div class="flex items-center gap-4 sm:gap-5 mb-5 sm:mb-6">
          <div class="w-14 h-14 sm:w-16 sm:h-16 bg-[#FF0000]/10 rounded-2xl flex items-center justify-center transition-transform group-hover:scale-110 shrink-0">
            <img 
              src="/images/development.png" 
              alt="Development" 
              class="w-8 h-8 sm:w-10 sm:h-10"
            />
          </div>
          <h2 class="text-2xl sm:text-3xl font-semibold">Development</h2>
        </div>
        
        <p class="text-sm sm:text-base text-white/70 leading-relaxed">
          I can build websites tailored to your exact needs — from concept to completion. 
          Whether starting from scratch or improving an existing idea, I’ll work closely with you throughout the process.
        </p>
      </div>

      <!-- Maintenance Card -->
      <div class="group bg-[#2E2A2A] border border-white/5 hover:border-white/20 rounded-3xl p-6 sm:p-10 transition-all duration-500 hover:-translate-y-2">
        <div class="flex items-center gap-4 sm:gap-5 mb-5 sm:mb-6">
          <div class="w-14 h-14 sm:w-16 sm:h-16 bg-[#FF0000]/10 rounded-2xl flex items-center justify-center transition-transform group-hover:scale-110 shrink-0">
            <img 
              src="/images/maintenance.png" 
              alt="Maintenance" 
              class="w-8 h-8 sm:w-10 sm:h-10"
            />
          </div>
          <h2 class="text-2xl sm:text-3xl font-semibold">Maintenance</h2>
        </div>
        
        <p class="text-sm sm:text-base text-white/70 leading-relaxed">
          Need fixes, updates, or ongoing support? I can maintain and improve your website, 
          ensuring it stays fast, secure, and up-to-date. I’ll always keep you in the loop.
        </p>
      </div>

    </div>
  </div>
</template>
