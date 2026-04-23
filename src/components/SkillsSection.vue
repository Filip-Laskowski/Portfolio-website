<script setup>
const categories = [
  {
    title: 'Languages',
    icon: 'M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5',
    skills: [
      { name: 'Python', level: 'Advanced' },
      { name: 'JavaScript', level: 'Advanced' },
      { name: 'HTML/CSS', level: 'Advanced' },
      { name: 'TypeScript', level: 'Intermediate' },
      { name: 'C++', level: 'Intermediate' },
      { name: 'C#', level: 'Intermediate' },
      { name: 'MATLAB', level: 'Intermediate' },
      { name: 'SQL', level: 'Intermediate' },
    ],
  },
  {
    title: 'Frameworks & Web',
    icon: 'M6.429 9.75L2.25 12l4.179 2.25m0-4.5l5.571 3 5.571-3m-11.142 0L2.25 7.5 12 2.25l9.75 5.25-4.179 2.25m0 0L12 12.75l-5.571-3m11.142 0L22.5 12l-4.929 2.25M12 12.75l5.571 3m-5.571-3v7.5m5.571-4.5L22.5 18l-9.75 5.25v-7.5',
    skills: [
      { name: 'Vue.js', level: 'Advanced' },
      { name: 'Pinia', level: 'Intermediate' },
      { name: 'Node.js', level: 'Advanced' },
      { name: 'Node-RED', level: 'Advanced' },
      { name: 'MySQL', level: 'Intermediate' },
      { name: 'Redis', level: 'Basic' },
    ],
  },
  {
    title: 'Machine Learning',
    icon: 'M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714c0 .597.237 1.17.659 1.591L19.8 15.3M14.25 3.104c.251.023.501.05.75.082M19.8 15.3l-1.57.393A9.065 9.065 0 0112 15a9.065 9.065 0 00-6.23.693L5 14.5m14.8.8l1.402 1.402c1.232 1.232.65 3.318-1.067 3.611A48.309 48.309 0 0112 21c-2.773 0-5.491-.235-8.135-.687-1.718-.293-2.3-2.379-1.067-3.61L5 14.5',
    skills: [
      { name: 'PyTorch', level: 'Intermediate' },
      { name: 'TensorFlow', level: 'Basic' },
      { name: 'OpenCV', level: 'Intermediate' },
      { name: 'Open3D', level: 'Intermediate' },
    ],
  },
  {
    title: 'Cloud & DevOps',
    icon: 'M2.25 15a4.5 4.5 0 004.5 4.5H18a3.75 3.75 0 001.332-7.257 3 3 0 00-3.758-3.848 5.25 5.25 0 00-10.233 2.33A4.502 4.502 0 002.25 15z',
    skills: [
      { name: 'AWS (EC2, S3, Cognito)', level: 'Intermediate' },
      { name: 'Docker', level: 'Intermediate' },
      { name: 'Git / GitHub', level: 'Advanced' },
    ],
  },
  {
    title: 'Robotics & Embedded',
    icon: 'M9.594 3.94c.09-.542.56-.94 1.11-.94h2.593c.55 0 1.02.398 1.11.94l.213 1.281c.063.374.313.686.645.87.074.04.147.083.22.127.325.196.72.257 1.075.124l1.217-.456a1.125 1.125 0 011.37.49l1.296 2.247a1.125 1.125 0 01-.26 1.431l-1.003.827c-.293.241-.438.613-.431.992a7 7 0 010 .255c-.007.378.138.75.43.991l1.004.827c.424.35.534.954.26 1.43l-1.298 2.247a1.125 1.125 0 01-1.369.491l-1.217-.456c-.355-.133-.75-.072-1.076.124a7 7 0 01-.22.128c-.331.183-.581.495-.644.869l-.213 1.28c-.09.543-.56.941-1.11.941h-2.594c-.55 0-1.02-.398-1.11-.94l-.213-1.281c-.062-.374-.312-.686-.644-.87a7 7 0 01-.22-.127c-.325-.196-.72-.257-1.076-.124l-1.217.456a1.125 1.125 0 01-1.369-.49l-1.297-2.247a1.125 1.125 0 01.26-1.431l1.004-.827c.292-.24.437-.613.43-.992a7 7 0 010-.255c.007-.378-.138-.75-.43-.991l-1.004-.827a1.125 1.125 0 01-.26-1.43l1.297-2.247a1.125 1.125 0 011.37-.491l1.216.456c.356.133.751.072 1.076-.124.072-.044.146-.087.22-.128.332-.183.582-.495.644-.869l.214-1.281z M15 12a3 3 0 11-6 0 3 3 0 016 0z',
    skills: [
      { name: 'ROS2', level: 'Intermediate' },
      { name: 'Embedded Systems', level: 'Intermediate' },
      { name: 'PID Control', level: 'Intermediate' },
      { name: 'Sensor Integration', level: 'Intermediate' },
    ],
  },
  {
    title: 'Design & Simulation',
    icon: 'M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L6.832 19.82a4.5 4.5 0 01-1.897 1.13l-2.685.8.8-2.685a4.5 4.5 0 011.13-1.897L16.863 4.487zm0 0L19.5 7.125',
    skills: [
      { name: 'Fusion 360', level: 'Intermediate' },
      { name: 'SolidWorks', level: 'Basic' },
      { name: 'Gazebo', level: 'Intermediate' },
      { name: 'Figma', level: 'Basic' },
    ],
  },
]

const levelStyle = {
  Advanced: 'text-accent',
  Intermediate: 'text-body',
  Basic: 'text-muted',
}
</script>

<template>
  <section id="skills" class="py-20 lg:py-32">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <!-- Section label -->
      <div v-reveal class="flex items-center gap-4 mb-16">
        <span class="font-mono text-sm text-accent">04</span>
        <span class="w-8 h-px bg-edge"></span>
        <span class="font-mono text-xs tracking-[0.2em] uppercase text-muted">Skills</span>
      </div>

      <h2 v-reveal="80" class="font-display text-2xl sm:text-3xl font-bold text-heading mb-12">
        Technical Toolkit
      </h2>

      <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5">
        <div
          v-for="(cat, i) in categories"
          :key="cat.title"
          v-reveal="80 + i * 60"
          class="bg-surface rounded-xl border border-edge/50 p-6 hover:border-edge transition-colors duration-300"
        >
          <div class="flex items-center gap-3 mb-5">
            <div class="w-9 h-9 rounded-lg bg-accent/10 flex items-center justify-center">
              <svg class="w-5 h-5 text-accent" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" :d="cat.icon" />
              </svg>
            </div>
            <h3 class="font-display text-sm font-semibold text-heading">{{ cat.title }}</h3>
          </div>

          <div class="space-y-2.5">
            <div
              v-for="skill in cat.skills"
              :key="skill.name"
              class="flex items-center justify-between"
            >
              <span class="text-sm text-body">{{ skill.name }}</span>
              <span :class="['font-mono text-[10px] tracking-wider', levelStyle[skill.level]]">
                {{ skill.level.toUpperCase() }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
