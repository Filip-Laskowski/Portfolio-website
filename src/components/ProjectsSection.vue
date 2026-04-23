<script setup>
import { ref, computed, watch } from 'vue'
import adjustedUmfImg from '../assets/AdjustedUMF.png'
import motorControllerImg from '../assets/EmbeddedMotorController.png'

const activeFilter = ref('All')
const selectedProject = ref(null)

const filters = ['All', 'Machine Learning', 'IoT', 'Robotics', 'Embedded', 'Software', 'Research']

const projects = [
  {
    title: 'Multimodal Machine Learning Thesis',
    subtitle: 'Honours Research',
    description:
      'Developing novel multimodal ML approaches using factorized contrastive learning to combine point cloud and image data for enhanced robotics and computer vision.',
    highlights: [
      'Factorized contrastive learning architecture',
      'Custom loss functions for cross-modal learning',
      'Applications in autonomous vehicles & robotics',
    ],
    technologies: ['PyTorch', 'Open3D', 'OpenCV', 'GPU Computing'],
    categories: ['Machine Learning', 'Research'],
    year: '2025\u201426',
    status: 'In Progress',
    statusColor: 'text-accent',
    image: adjustedUmfImg,
    imageCaption: 'Adjusted UMF architecture for confidence-weighted cross-attention on corrupt data',
  },
  {
    title: 'IoT Leak Detection Platform',
    subtitle: 'Leakster \u2014 Industry',
    description:
      'Full-stack platform for industrial leak detection using IoT sensors and machine learning classifiers for anomaly detection.',
    highlights: [
      'Real-time sensor data visualization',
      'ML classifiers for anomaly detection',
      'Scalable RESTful API architecture',
    ],
    technologies: ['Vue.js', 'Node.js', 'MySQL', 'Docker', 'PyTorch'],
    categories: ['IoT', 'Machine Learning'],
    year: '2023\u2014Now',
    status: 'Industry',
    statusColor: 'text-green-400',
  },
  {
    title: 'Autonomous Warehouse Robot',
    subtitle: 'Academic \u2014 Lead Developer',
    description:
      'Miniature autonomous robot with pathfinding, navigation, and order collection from warehouse shelves.',
    highlights: [
      'A* and Dijkstra pathfinding algorithms',
      'Sensor fusion for navigation',
      'Multi-subsystem control software',
    ],
    technologies: ['C/C++', 'Embedded', 'Fusion 360', 'Sensors'],
    categories: ['Robotics', 'Embedded'],
    year: '2022\u201423',
    status: 'Academic',
    statusColor: 'text-purple-400',
  },
  {
    title: 'Embedded Motor Controller',
    subtitle: 'Academic \u2014 Individual',
    description:
      'Embedded controller for 3-phase industrial motor with speed control and real-time temperature monitoring.',
    highlights: [
      'Speed control with real-time feedback',
      'Temperature monitoring & safety shutdowns',
      'Interrupt-driven phase timing',
    ],
    technologies: ['C/C++', 'Embedded', 'PWM', 'Power Electronics'],
    categories: ['Embedded'],
    year: '2022\u201423',
    status: 'Academic',
    statusColor: 'text-purple-400',
    image: motorControllerImg,
    imageCaption: 'Layered RTOS architecture — HW, ISR, Tasks, and Functions layers with I2C/SPI/ADC interfaces',
  },
  {
    title: 'PID Line Follower Robot',
    subtitle: 'Academic \u2014 Lead Developer',
    description:
      'Autonomous line-following robot with PID control system for precise path tracking and minimal oscillation.',
    highlights: [
      'PID control with systematic tuning',
      'Optimized chassis weight distribution',
      'Accurate path following',
    ],
    technologies: ['C/C++', 'Arduino', 'PID Control', 'IR Sensors'],
    categories: ['Robotics', 'Embedded'],
    year: '2022\u201423',
    status: 'Academic',
    statusColor: 'text-purple-400',
  },
  {
    title: 'Motorsports Simulation',
    subtitle: 'Extracurricular',
    description:
      'Enhanced Gazebo simulation environment for motorsports applications with Lidar and depth camera integration.',
    highlights: [
      'Lidar & depth camera integration',
      '~40% performance optimization',
      'Updated ROS2 component structure',
    ],
    technologies: ['ROS2', 'Gazebo', 'Linux', 'Sensors'],
    categories: ['Robotics', 'Research'],
    year: '2023',
    status: 'Club',
    statusColor: 'text-amber-400',
  },
  {
    title: 'Home Server & Productivity Tracker',
    subtitle: 'Personal Project',
    description:
      'Turned a mini PC into an always-on self-hosted server running a productivity and calorie tracking web app, accessible from anywhere in the world via Tailscale VPN — no port forwarding, no cloud.',
    highlights: [
      'Zero-dependency Python backend with SQLite — no frameworks',
      'Systemd service with auto-restart on crash or reboot',
      'Global access via Tailscale encrypted VPN with MagicDNS',
      'Focus timer, task manager, calorie tracker & 14-day stats',
    ],
    technologies: ['Python', 'SQLite', 'Linux', 'Tailscale', 'Systemd', 'Vanilla JS'],
    categories: ['Software', 'IoT'],
    year: '2025',
    status: 'Personal',
    statusColor: 'text-cyan-400',
  },
  {
    title: 'Visual Place Recognition',
    subtitle: 'Academic Research',
    description:
      'Comparative study on Visual Place Recognition using VLAD and SIFT algorithms with performance evaluation.',
    highlights: [
      'VLAD and SIFT implementation',
      'Visual place recognition dictionaries',
      'Performance evaluation framework',
    ],
    technologies: ['Python', 'OpenCV', 'Computer Vision'],
    categories: ['Research', 'Machine Learning'],
    year: '2023',
    status: 'Research',
    statusColor: 'text-blue-400',
  },
]

const filteredProjects = computed(() => {
  if (activeFilter.value === 'All') return projects
  return projects.filter((p) => p.categories.includes(activeFilter.value))
})

function openProject(project) {
  selectedProject.value = project
  document.body.style.overflow = 'hidden'
}

function closeModal() {
  selectedProject.value = null
  document.body.style.overflow = ''
}

function onBackdropClick(e) {
  if (e.target === e.currentTarget) closeModal()
}

watch(selectedProject, (val) => {
  if (!val) document.body.style.overflow = ''
})
</script>

<template>
  <section id="projects" class="py-20 lg:py-32">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <!-- Section label -->
      <div v-reveal class="flex items-center gap-4 mb-16">
        <span class="font-mono text-sm text-accent">03</span>
        <span class="w-8 h-px bg-edge"></span>
        <span class="font-mono text-xs tracking-[0.2em] uppercase text-muted">Projects</span>
      </div>

      <h2 v-reveal="80" class="font-display text-2xl sm:text-3xl font-bold text-heading mb-10">
        What I've Built
      </h2>

      <!-- Filters -->
      <div v-reveal="120" class="flex flex-wrap gap-2 mb-12">
        <button
          v-for="filter in filters"
          :key="filter"
          :class="[
            'px-4 py-2 text-xs font-mono tracking-wider rounded-lg transition-all duration-300',
            activeFilter === filter
              ? 'bg-accent text-white'
              : 'text-muted border border-edge hover:border-accent/40 hover:text-body',
          ]"
          @click="activeFilter = filter"
        >
          {{ filter.toUpperCase() }}
        </button>
      </div>

      <!-- Grid -->
      <TransitionGroup
        tag="div"
        class="grid md:grid-cols-2 gap-5"
        enter-active-class="transition-all duration-400 ease-out"
        enter-from-class="opacity-0 translate-y-4"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition-all duration-300 ease-in"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 translate-y-4"
      >
        <article
          v-for="project in filteredProjects"
          :key="project.title"
          :class="[
            'group bg-surface border border-edge/50 rounded-xl p-6 hover:border-accent/30 transition-all duration-300 hover:shadow-[0_0_40px_-8px_rgba(255,107,53,0.1)]',
            project.image ? 'cursor-pointer' : '',
          ]"
          @click="project.image ? openProject(project) : null"
        >
          <div class="flex items-start justify-between gap-3 mb-3">
            <div>
              <h3 class="text-base font-semibold text-heading group-hover:text-accent transition-colors duration-300">
                {{ project.title }}
              </h3>
              <p class="text-xs text-muted mt-0.5">{{ project.subtitle }}</p>
            </div>
            <div class="flex items-center gap-2 shrink-0">
              <svg
                v-if="project.image"
                class="w-4 h-4 text-muted group-hover:text-accent transition-colors duration-300"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                stroke-width="1.5"
              >
                <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 3.75v4.5m0-4.5h4.5m-4.5 0L9 9M3.75 20.25v-4.5m0 4.5h4.5m-4.5 0L9 15M20.25 3.75h-4.5m4.5 0v4.5m0-4.5L15 9m5.25 11.25h-4.5m4.5 0v-4.5m0 4.5L15 15" />
              </svg>
              <span :class="['font-mono text-[10px] tracking-wider', project.statusColor]">
                {{ project.status.toUpperCase() }}
              </span>
            </div>
          </div>

          <p class="text-sm text-body leading-relaxed mb-4">{{ project.description }}</p>

          <ul class="space-y-1.5 mb-5">
            <li
              v-for="h in project.highlights"
              :key="h"
              class="flex items-start gap-2 text-sm text-body"
            >
              <svg class="w-3.5 h-3.5 text-accent mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
              </svg>
              {{ h }}
            </li>
          </ul>

          <div class="flex items-end justify-between gap-4 pt-4 border-t border-edge/30">
            <div class="flex flex-wrap gap-1.5">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="px-2 py-0.5 text-[11px] text-muted bg-base rounded border border-edge/50"
              >
                {{ tech }}
              </span>
            </div>
            <span class="font-mono text-[11px] text-muted shrink-0">{{ project.year }}</span>
          </div>
        </article>
      </TransitionGroup>
    </div>
  </section>

  <!-- Project Modal -->
  <Teleport to="body">
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
    >
      <div
        v-if="selectedProject"
        class="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-6"
        @click="onBackdropClick"
        @keydown.escape="closeModal"
      >
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-black/70 backdrop-blur-sm"></div>

        <!-- Modal -->
        <div class="relative w-full max-w-3xl max-h-[90vh] overflow-y-auto bg-surface rounded-2xl border border-edge/50 shadow-2xl">
          <!-- Close button -->
          <button
            class="absolute top-4 right-4 z-10 w-8 h-8 flex items-center justify-center rounded-full bg-base/80 border border-edge/50 text-muted hover:text-heading hover:border-edge transition-colors"
            @click="closeModal"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>

          <!-- Image -->
          <div v-if="selectedProject.image" class="p-6 pb-0">
            <div class="rounded-xl overflow-hidden bg-white p-4 sm:p-6">
              <img
                :src="selectedProject.image"
                :alt="selectedProject.title"
                class="w-full object-contain max-h-[50vh]"
              />
            </div>
            <p v-if="selectedProject.imageCaption" class="text-xs text-muted mt-3 text-center italic">
              {{ selectedProject.imageCaption }}
            </p>
          </div>

          <!-- Content -->
          <div class="p-6">
            <div class="flex items-start justify-between gap-3 mb-2">
              <div>
                <h3 class="font-display text-xl font-bold text-heading">
                  {{ selectedProject.title }}
                </h3>
                <p class="text-sm text-muted mt-0.5">{{ selectedProject.subtitle }}</p>
              </div>
              <span :class="['shrink-0 font-mono text-[10px] tracking-wider mt-1', selectedProject.statusColor]">
                {{ selectedProject.status.toUpperCase() }}
              </span>
            </div>

            <p class="text-body leading-relaxed mt-4">{{ selectedProject.description }}</p>

            <ul class="space-y-2 mt-6">
              <li
                v-for="h in selectedProject.highlights"
                :key="h"
                class="flex items-start gap-2.5 text-sm text-body"
              >
                <svg class="w-4 h-4 text-accent mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                </svg>
                {{ h }}
              </li>
            </ul>

            <div class="flex flex-wrap items-center gap-2 mt-6 pt-4 border-t border-edge/30">
              <span class="font-mono text-[10px] tracking-wider uppercase text-muted mr-1">Stack</span>
              <span
                v-for="tech in selectedProject.technologies"
                :key="tech"
                class="px-2.5 py-1 text-xs text-body bg-base rounded border border-edge/50"
              >
                {{ tech }}
              </span>
              <span class="ml-auto font-mono text-xs text-muted">{{ selectedProject.year }}</span>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>
