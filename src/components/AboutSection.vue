<script setup>
const education = [
  {
    school: 'Queensland University of Technology',
    degree: 'Bachelor of Engineering (Honours) — Mechatronics',
    period: 'Feb 2022 — Jun 2026',
    location: 'Brisbane, Australia',
    details: [
      'GPA: 6.25 / 7.0',
      "Executive Dean's Commendation for Academic Excellence (2024, 2025)",
    ],
    thesis:
      'Multimodal Machine Learning with Factorized Contrastive Learning — developing novel approaches for fusing point cloud and image data.',
    coursework: [
      'Embedded Systems',
      'Robotics & Automation',
      'Control Systems',
      'Machine Learning',
      'Digital Signal Processing',
    ],
  },
  {
    school: 'Nanyang Technological University, Singapore',
    degree: 'Artificial Intelligence Summer Program',
    period: 'Jun 2023 — Aug 2023',
    location: 'Singapore',
    details: [
      'International exchange covering ML fundamentals, neural networks, deep learning, computer vision, and NLP.',
    ],
  },
]

const awards = [
  { title: "Executive Dean's Commendation", org: 'QUT', year: '2025' },
  { title: "Executive Dean's Commendation", org: 'QUT', year: '2024' },
]

const focusAreas = [
  'Controls Engineering',
  'Industrial Automation',
  'PLC Programming',
  'SCADA Systems',
  'IoT & Sensors',
  'Machine Learning',
  'Robotics',
]

const learning = [
  'RF Engineering (RTL-SDR)',
  'Advanced Control Systems',
  'Industrial Protocols',
]
</script>

<template>
  <section id="about" class="py-20 lg:py-32">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <!-- Section label -->
      <div v-reveal class="flex items-center gap-4 mb-16">
        <span class="font-mono text-sm text-accent">01</span>
        <span class="w-8 h-px bg-edge"></span>
        <span class="font-mono text-xs tracking-[0.2em] uppercase text-muted">About</span>
      </div>

      <div class="grid lg:grid-cols-5 gap-12 lg:gap-16">
        <!-- Bio -->
        <div class="lg:col-span-3">
          <h2 v-reveal class="font-display text-2xl sm:text-3xl font-bold text-heading mb-8">
            Bridging software and<br class="hidden sm:block" />physical systems
          </h2>
          <div class="space-y-4">
            <p v-reveal="80" class="text-body leading-relaxed">
              I am a final year Mechatronics Engineering (Honours) student at
              Queensland University of Technology, on track to graduate in June 2026
              with a GPA of 6.25.
            </p>
            <p v-reveal="120" class="text-body leading-relaxed">
              Since October 2023, I have been working at Leakster as a Software
              Engineer, developing full-stack IoT platforms for industrial clients. My
              work includes building backend systems in Python and Node.js, designing
              data pipelines for real-time sensor data, and developing machine learning
              classifiers using PyTorch to distinguish leak events from ambient pipeline
              noise.
            </p>
            <p v-reveal="160" class="text-body leading-relaxed">
              Through my degree I have built autonomous warehouse robots with
              pathfinding algorithms, line-following robots with PID control, and
              embedded motor controllers with safety monitoring. I have also contributed
              to robotics simulation projects using ROS2 and Gazebo, and conducted
              computer vision research on visual place recognition.
            </p>
            <p v-reveal="200" class="text-body leading-relaxed">
              I am seeking graduate roles in controls engineering, industrial
              automation, SCADA, and PLC-based systems where I can apply my combined
              software and mechatronics background.
            </p>
          </div>
        </div>

        <!-- Sidebar -->
        <div class="lg:col-span-2 space-y-10">
          <!-- Awards -->
          <div v-reveal>
            <h3 class="font-mono text-xs tracking-[0.15em] uppercase text-muted mb-4">Awards</h3>
            <div class="space-y-3">
              <div
                v-for="award in awards"
                :key="award.year"
                class="flex items-start gap-3 p-3 bg-surface rounded-lg border border-edge/50"
              >
                <svg class="w-4 h-4 text-accent mt-0.5 shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path d="M10 1l2.39 4.845 5.345.777-3.867 3.77.913 5.323L10 13.347l-4.781 2.368.913-5.323-3.867-3.77 5.345-.777L10 1z" />
                </svg>
                <div>
                  <p class="text-sm text-heading">{{ award.title }}</p>
                  <p class="text-xs text-muted mt-0.5">{{ award.org }} &middot; {{ award.year }}</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Focus Areas -->
          <div v-reveal="80">
            <h3 class="font-mono text-xs tracking-[0.15em] uppercase text-muted mb-4">Focus Areas</h3>
            <div class="flex flex-wrap gap-2">
              <span
                v-for="area in focusAreas"
                :key="area"
                class="px-3 py-1.5 text-xs text-body bg-surface rounded-full border border-edge/50"
              >
                {{ area }}
              </span>
            </div>
          </div>

          <!-- Currently Learning -->
          <div v-reveal="160">
            <h3 class="font-mono text-xs tracking-[0.15em] uppercase text-muted mb-4">Currently Learning</h3>
            <ul class="space-y-2.5">
              <li
                v-for="item in learning"
                :key="item"
                class="flex items-center gap-2.5 text-sm text-body"
              >
                <span class="w-1 h-1 bg-accent rounded-full"></span>
                {{ item }}
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Education Timeline -->
      <div class="mt-20 lg:mt-24">
        <h3 v-reveal class="font-display text-xl font-bold text-heading mb-10">Education</h3>
        <div class="space-y-6">
          <div
            v-for="(edu, i) in education"
            :key="edu.school"
            v-reveal="i * 100"
            class="relative pl-8 border-l border-edge"
          >
            <div class="absolute -left-[5px] top-2 w-2.5 h-2.5 bg-accent rounded-full ring-4 ring-base"></div>

            <div class="bg-surface rounded-xl p-6 border border-edge/50">
              <div class="flex flex-wrap items-start justify-between gap-2 mb-3">
                <div>
                  <h4 class="text-base font-semibold text-heading">{{ edu.school }}</h4>
                  <p class="text-sm text-accent mt-0.5">{{ edu.degree }}</p>
                </div>
                <div class="text-right">
                  <p class="font-mono text-xs text-muted">{{ edu.period }}</p>
                  <p class="text-xs text-muted">{{ edu.location }}</p>
                </div>
              </div>

              <ul class="space-y-1.5">
                <li
                  v-for="detail in edu.details"
                  :key="detail"
                  class="flex items-start gap-2 text-sm text-body"
                >
                  <svg class="w-4 h-4 text-accent mt-0.5 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                  </svg>
                  {{ detail }}
                </li>
              </ul>

              <div v-if="edu.thesis" class="mt-4 p-3 bg-accent/5 rounded-lg border border-accent/10">
                <p class="font-mono text-[10px] tracking-wider uppercase text-accent mb-1">Honours Thesis</p>
                <p class="text-sm text-body">{{ edu.thesis }}</p>
              </div>

              <div v-if="edu.coursework" class="mt-4 flex flex-wrap gap-1.5">
                <span
                  v-for="course in edu.coursework"
                  :key="course"
                  class="px-2 py-0.5 text-[11px] text-muted bg-base rounded border border-edge/50"
                >
                  {{ course }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
