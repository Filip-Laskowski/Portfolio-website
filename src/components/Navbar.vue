<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileOpen = ref(false)

const links = [
  { label: 'About', href: '#about' },
  { label: 'Experience', href: '#experience' },
  { label: 'Projects', href: '#projects' },
  { label: 'Skills', href: '#skills' },
  { label: 'Contact', href: '#contact' },
]

function handleScroll() {
  isScrolled.value = window.scrollY > 20
}

function closeMobile() {
  mobileOpen.value = false
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-500',
      isScrolled
        ? 'bg-base/80 backdrop-blur-xl border-b border-subtle'
        : 'bg-transparent',
    ]"
  >
    <div class="max-w-6xl mx-auto px-6 lg:px-8 h-16 flex items-center justify-between">
      <a
        href="#hero"
        class="font-display font-bold text-lg text-heading tracking-tight hover:text-accent transition-colors duration-300"
      >
        FL<span class="text-accent">.</span>
      </a>

      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="relative text-sm text-muted hover:text-heading transition-colors duration-300 py-1 after:absolute after:bottom-0 after:left-0 after:w-0 after:h-px after:bg-accent after:transition-all after:duration-300 hover:after:w-full"
        >
          {{ link.label }}
        </a>
        <a
          href="#contact"
          class="text-sm font-medium px-5 py-2 bg-accent text-white rounded-lg hover:bg-accent-hover transition-all duration-300 hover:shadow-lg hover:shadow-accent/20"
        >
          Get in Touch
        </a>
      </div>

      <button
        class="md:hidden p-2 text-body hover:text-heading transition-colors"
        @click="mobileOpen = !mobileOpen"
        aria-label="Toggle menu"
      >
        <svg v-if="!mobileOpen" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <Transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div
        v-if="mobileOpen"
        class="md:hidden bg-surface/95 backdrop-blur-xl border-b border-edge px-6 pb-4"
      >
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="block py-3 text-sm text-body hover:text-accent transition-colors border-b border-subtle last:border-0"
          @click="closeMobile"
        >
          {{ link.label }}
        </a>
      </div>
    </Transition>
  </nav>
</template>
