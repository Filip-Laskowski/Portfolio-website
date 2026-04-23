<script setup>
const experiences = [
  {
    role: 'Software Engineer',
    company: 'Leakster',
    description: 'Developing full-stack IoT platforms for industrial leak detection systems.',
    period: 'Oct 2023 — Present',
    location: 'Remote',
    current: true,
    responsibilities: [
      'Develop and maintain full-stack web platform using Vue.js, Pinia, Node.js, and Docker',
      'Design and implement RESTful APIs in Node-RED for secure database communication',
      'Manage and optimize MySQL database structures for scalable IoT data storage',
      'Create comprehensive API documentation for database interfaces',
    ],
    achievements: [
      'Built complete full-stack platform enabling real-time visualization of IoT sensor data',
      'Trained ML classifier using PyTorch to distinguish leak events from ambient pipeline noise',
      'Developed clustering algorithm for leak detection through iterative testing',
      'Optimized database queries to support scalable data storage and retrieval',
    ],
    technologies: ['Vue.js', 'Pinia', 'Node.js', 'Node-RED', 'MySQL', 'Docker', 'PyTorch', 'Python', 'AWS'],
  },
  {
    role: 'Research Assistant',
    company: 'Queensland University of Technology',
    description: 'Vacation Research Experience Scheme (VRES) — investigating Visual Place Recognition techniques for robotics navigation.',
    period: 'Nov 2023 — Feb 2024',
    location: 'Brisbane, QLD',
    current: false,
    responsibilities: [
      'Implemented VLAD and SIFT-based Visual Place Recognition pipelines from research literature',
      'Designed and ran quantitative performance evaluations across benchmark datasets',
      'Built visual place recognition dictionaries for environment representation',
      'Documented findings and methodology in a formal research report',
    ],
    achievements: [
      'Delivered comparative analysis of VLAD vs SIFT recognition accuracy and runtime performance',
      'Gained hands-on experience applying computer vision theory to real robotics problems',
      'Contributed to ongoing research in autonomous navigation at QUT',
    ],
    technologies: ['Python', 'OpenCV', 'NumPy', 'Computer Vision', 'Linux'],
  },
]
</script>

<template>
  <section id="experience" class="py-20 lg:py-32">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <!-- Section label -->
      <div v-reveal class="flex items-center gap-4 mb-16">
        <span class="font-mono text-sm text-accent">02</span>
        <span class="w-8 h-px bg-edge"></span>
        <span class="font-mono text-xs tracking-[0.2em] uppercase text-muted">Experience</span>
      </div>

      <!-- Experience cards -->
      <div class="space-y-6">
        <div
          v-for="(exp, i) in experiences"
          :key="exp.company"
          v-reveal="80 + i * 60"
          class="bg-surface rounded-2xl border border-edge/50 overflow-hidden"
        >
          <!-- Header -->
          <div class="p-6 sm:p-8">
            <div class="flex flex-wrap items-start justify-between gap-4">
              <div>
                <h3 class="font-display text-xl sm:text-2xl font-bold text-heading">{{ exp.role }}</h3>
                <p class="text-accent font-medium mt-1">{{ exp.company }}</p>
                <p class="text-sm text-muted mt-2">{{ exp.description }}</p>
              </div>
              <div class="text-right">
                <div v-if="exp.current" class="inline-flex items-center gap-2 px-3 py-1.5 bg-green-500/10 border border-green-500/20 rounded-full">
                  <span class="relative flex h-1.5 w-1.5">
                    <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400/75"></span>
                    <span class="relative inline-flex rounded-full h-1.5 w-1.5 bg-green-400"></span>
                  </span>
                  <span class="font-mono text-xs text-green-400">CURRENT</span>
                </div>
                <div v-else class="inline-flex items-center px-3 py-1.5 bg-blue-500/10 border border-blue-500/20 rounded-full">
                  <span class="font-mono text-xs text-blue-400">RESEARCH</span>
                </div>
                <p class="font-mono text-xs text-muted mt-2">{{ exp.period }}</p>
                <p class="text-xs text-muted">{{ exp.location }}</p>
              </div>
            </div>
          </div>

          <div class="border-t border-edge/30"></div>

          <!-- Split content -->
          <div class="grid md:grid-cols-2">
            <div class="p-6 sm:p-8">
              <h4 class="font-mono text-xs tracking-[0.15em] uppercase text-muted mb-5">Responsibilities</h4>
              <ul class="space-y-3">
                <li
                  v-for="item in exp.responsibilities"
                  :key="item"
                  class="flex items-start gap-3 text-sm text-body"
                >
                  <svg class="w-4 h-4 text-muted mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                  </svg>
                  {{ item }}
                </li>
              </ul>
            </div>

            <div class="p-6 sm:p-8 border-t md:border-t-0 md:border-l border-edge/30">
              <h4 class="font-mono text-xs tracking-[0.15em] uppercase text-muted mb-5">Key Achievements</h4>
              <ul class="space-y-3">
                <li
                  v-for="item in exp.achievements"
                  :key="item"
                  class="flex items-start gap-3 text-sm text-body"
                >
                  <svg class="w-4 h-4 text-accent mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                  </svg>
                  {{ item }}
                </li>
              </ul>
            </div>
          </div>

          <!-- Tech footer -->
          <div class="px-6 sm:px-8 py-4 bg-base/50 border-t border-edge/30">
            <div class="flex flex-wrap items-center gap-2">
              <span class="font-mono text-[10px] tracking-wider uppercase text-muted mr-2">Stack</span>
              <span
                v-for="tech in exp.technologies"
                :key="tech"
                class="px-2.5 py-1 text-xs text-body bg-surface rounded border border-edge/50"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
