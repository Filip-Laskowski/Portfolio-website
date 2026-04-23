<script setup>
const stats = [
  { value: '6.25', label: 'GPA / 7.0' },
  { value: '2+', label: 'Years Industry Experience' },
  { value: '7+', label: 'Projects Built' },
]
</script>

<template>
  <section id="hero" class="min-h-screen flex flex-col justify-center relative overflow-hidden">
    <!-- Dot grid -->
    <div
      class="absolute inset-0"
      style="background-image: radial-gradient(circle, rgba(255,255,255,0.035) 1px, transparent 1px); background-size: 24px 24px"
    ></div>

    <!-- Warm ambient glow -->
    <div class="absolute top-1/4 right-0 w-[500px] h-[500px] bg-accent/[0.04] rounded-full blur-[150px]"></div>

    <div class="relative max-w-6xl mx-auto px-6 lg:px-8 w-full pt-32 pb-20">
      <!-- Status badge -->
      <div v-reveal class="inline-flex items-center gap-2.5 px-4 py-2 bg-accent/10 border border-accent/20 rounded-full mb-10">
        <span class="relative flex h-2 w-2">
          <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-accent/75"></span>
          <span class="relative inline-flex rounded-full h-2 w-2 bg-accent"></span>
        </span>
        <span class="font-mono text-xs tracking-wider text-accent">OPEN TO OPPORTUNITIES</span>
      </div>

      <!-- Name -->
      <h1 v-reveal="80" class="font-display font-extrabold text-heading leading-[0.9] tracking-[-0.03em]">
        <span class="block text-5xl sm:text-7xl lg:text-[6.5rem]">FILIP</span>
        <span class="block text-[2.6rem] sm:text-7xl lg:text-[6.5rem] mt-1 sm:mt-2">LASKOWSKI</span>
      </h1>

      <!-- Tagline -->
      <div v-reveal="160" class="mt-8 max-w-xl">
        <p class="text-lg sm:text-xl text-body font-light leading-relaxed">
          Mechatronics Engineering meets
          <span class="text-heading font-normal">Software Development.</span>
        </p>
        <p class="mt-3 text-sm sm:text-base text-muted leading-relaxed">
          Building systems that connect software to the physical world — from IoT
          platforms and ML classifiers to autonomous robots and embedded controllers.
        </p>
      </div>

      <!-- CTAs -->
      <div v-reveal="240" class="flex flex-wrap gap-4 mt-10">
        <a
          href="#projects"
          class="group inline-flex items-center gap-2 px-6 py-3 bg-accent text-white text-sm font-medium rounded-lg hover:bg-accent-hover transition-all duration-300 hover:shadow-lg hover:shadow-accent/25"
        >
          View My Work
          <svg class="w-4 h-4 transition-transform duration-300 group-hover:translate-x-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </a>
        <a
          href="#contact"
          class="px-6 py-3 border border-edge text-body text-sm font-medium rounded-lg hover:border-accent/40 hover:text-heading transition-all duration-300"
        >
          Get in Touch
        </a>
      </div>

      <!-- Stats -->
      <div v-reveal="320" class="mt-20 pt-8 border-t border-edge/50">
        <div class="flex flex-wrap gap-8 sm:gap-0">
          <div v-for="(stat, i) in stats" :key="stat.label" class="flex items-center">
            <div v-if="i > 0" class="hidden sm:block w-px h-10 bg-edge/50 mx-12"></div>
            <div>
              <span class="font-mono text-2xl sm:text-3xl font-bold text-heading">{{ stat.value }}</span>
              <span class="block text-xs sm:text-sm text-muted mt-1">{{ stat.label }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll line -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2">
      <div class="w-px h-12 bg-gradient-to-b from-transparent to-edge"></div>
    </div>
  </section>
</template>
