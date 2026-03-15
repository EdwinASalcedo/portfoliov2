<template>
  <div>
    <HeroSection :data="hero" id="about" />

    <!-- Sections: full-width panels separated by gap (page bg shows through) -->
    <div class="flex flex-col gap-3 max-md:gap-2">

      <!-- Featured Apps -->
      <section id="apps" class="bg-apple-gray dark:bg-apple-charcoal py-20 scroll-mt-15 overflow-x-hidden max-md:py-15">
        <div class="max-w-245 mx-auto px-5.5 overflow-x-hidden max-md:px-4">
          <div class="text-center mb-15 max-md:mb-10">
            <h2 class="text-[48px] font-semibold tracking-[-0.015em] mb-3 text-neutral-900 dark:text-neutral-100 max-md:text-[36px]">Featured Apps</h2>
            <p class="text-[21px] text-neutral-500 dark:text-neutral-400 font-normal tracking-[-0.01em] max-md:text-[17px]">Available on the App Store</p>
          </div>
          <FeaturedApps :apps="featuredApps" />
        </div>
      </section>

      <!-- Experience + Education row -->
      <div class="grid grid-cols-2 gap-3 max-md:grid-cols-1">

        <!-- Experience -->
        <section id="experience" class="bg-apple-gray dark:bg-apple-charcoal py-20 scroll-mt-15 max-md:py-15">
          <div class="px-32 max-md:px-4">
            <div class="mb-12 max-md:mb-8">
              <h2 class="text-[48px] font-semibold tracking-[-0.015em] text-neutral-900 dark:text-white max-md:text-[36px] text-center">Experience</h2>
            </div>
            <TimelineComponent :items="experiences" :collapsible="true" />
          </div>
        </section>

        <!-- Education -->
        <section id="education" class="relative overflow-hidden scroll-mt-15 py-24 max-md:py-16">
          <img src="/screenshots/ufbg.webp" alt="" class="absolute inset-0 w-full h-full object-cover object-center" aria-hidden="true" />
          <div class="absolute inset-0 bg-linear-to-r from-black/90 via-black/80 to-transparent max-md:bg-black/70"></div>
          <div class="relative z-10 px-12 max-md:px-8">
            <h2 class="text-[48px] font-semibold tracking-[-0.015em] mb-8 text-white max-md:text-[36px] text-center">Education</h2>
            <div class="flex flex-col gap-8">
              <div v-for="(item, index) in education" :key="index">
                <h3 class="text-[28px] font-semibold tracking-[-0.01em] text-white mb-1">{{ item.title }}</h3>
                <p class="text-[19px] text-neutral-100 mb-1">{{ item.company }}</p>
                <p class="text-[15px] text-neutral-100 mb-3">{{ item.date }}</p>
                <p class="text-[18px] leading-normal text-neutral-100">{{ item.description }}</p>
              </div>
            </div>
          </div>
        </section>

      </div>

      <!-- Projects & Skills -->
      <section id="projects" class="bg-apple-gray dark:bg-apple-charcoal py-20 scroll-mt-15 max-md:py-15">
        <div class="text-center mb-15 max-md:mb-10">
          <h2 class="text-[48px] font-semibold tracking-[-0.015em] mb-3 text-neutral-900 dark:text-neutral-100 max-md:text-[36px]">Projects & Skills</h2>
        </div>
        <ProjectCarousel :items="projects" />
      </section>

    </div>

    <!-- Footer: flush to all edges, no gap -->
    <FooterSection name="Edwin Salcedo" email="edwin.a.salcedo02@gmail.com" />
  </div>
</template>

<script>
import HeroSection from '@/components/HeroSection.vue'
import TimelineComponent from '@/components/TimelineComponent.vue'
import ProjectCarousel from '@/components/ProjectCarousel.vue'
import FeaturedApps from '@/components/FeaturedApps.vue'
import FooterSection from '@/components/FooterSection.vue'

export default {
  name: 'HomeView',
  components: {
    HeroSection,
    TimelineComponent,
    ProjectCarousel,
    FeaturedApps,
    FooterSection
  },
  data() {
    return {
      hero: {
        name: 'Edwin Salcedo',
        title: 'iOS Software Engineer',
        description: 'Crafting intuitive and functional experiences that make a difference. Passionate about app architecture, user experience, and building products people love. Now learning graphics programming using the Metal framework by Apple'
      },
      experiences: [
        {
          title: 'iOS Software Engineer',
          company: 'Word O\' Mouth (Founder)',
          date: 'January 2026 - Present',
          logo: '/app_icons/WOM_logo.png',
          logoClass: 'rounded-[14px]',
          description: '• Architected and launched a social food discovery app from scratch, enabling users to share food reviews and locations (MapKit) with followers through a personalized feed \n• Selected Supabase over Firebase for backend infrastructure, leveraging PostgreSQL RLS policies and triggers to automate data syncing, reducing client-side code by 30% \n• Leading beta releases via TestFlight to 20+ users, collecting feedback to prioritize waht features to ship \n• Utilizing Swift concurrency (async/await) to handle Supabase Auth, Storage, and Database'
        },
        {
          title: 'GIS Data Scientist Intern',
          company: 'UF IFAS Ecosystem Services A.I Lab',
          date: 'May 2024 - September 2024',
          logo: '/icons/UF_Monogram.svg',
          logoClass: '',
          description: '• Built python scripts using Google Earth Engine, OpenStreetMap, GeoPandas, and geemap to extract, filter, and visualize Florida geospatial data for AI model training\n• Documented the data pipeline and script usage, writing clear setup and usage instructions for future lab members to reproduce and build upon the work\n• Presented findings through a technical slideshow, contributing to the professor\'s conference presentation, which spurred external interest and new research partnerships\n• Researched data collection methodologies in the early project phase, analyzing academic literature to design an effective approach to satellite imagery labeling for AI modeling'
        },
      ],
      projects: [
        {
          title: 'Word O\' Mouth',
          subtitle: 'iOS App',
          date: 'TestFlight Beta',
          description: 'Never have food FOMO again! Explore friend food recommendations on the map or leave reviews of your own',
          tags: ['SwiftUI', 'MapKit', 'Firebase Database, Analytics, Storage, Auth',],
          icon: '/icons/github.svg',
          link: 'https://github.com/EdwinASalcedo/MunchIn'
        },
        {
          title: 'MoodJo',
          subtitle: 'iOS App',
          date: '2026',
          description: 'Record your daily mood along with a journal entry. Entries can include a picture, audio snippet, or text. View monthly and weekly mood summaries',
          tags: ['SwiftUI', 'SwiftData', 'AVFoundation', 'Metal'],
          icon: '/icons/github.svg',
          link: ''
        },
        {
          title: 'LiftNotes',
          subtitle: 'iOS App',
          date: '2025',
          description: 'An app to record your lifts in the gym. Stay on track and make gains! Allows for users to create workout templates, create exercises as needed, and view workout history',
          tags: ['SwiftUI', 'SwiftData', 'Swift',],
          icon: '/icons/github.svg',
          link: 'https://github.com/EdwinASalcedo/LiftLogSwiftData'
        },
        {
          title: 'A.I Chat App',
          subtitle: 'iOS App',
          date: '2025',
          description: 'Create your own avatars or use other user-made avatars to chat with! App built with MVVM architecture, uses OpenAI API for chat and image generation',
          tags: ['SwiftUI', 'OpenAI API', 'RevenueCat', 'Firebase Database, Analytics, Storage, Auth',],
          icon: '/icons/github.svg',
          link: 'https://github.com/EdwinASalcedo/AIChat'
        },
        {
          title: 'OpenGL',
          subtitle: '3D Graphics Programming',
          date: '2025',
          description: 'Learned how to load models, implement lighting, toggle textures, and integrate camera controls',
          tags: ['OpenGL', 'GLSL', 'C++'],
          icon: '/icons/github.svg',
          link: 'https://github.com/EdwinASalcedo/OpenGLTextureToggler'
        },
        {
          title: 'Toy Dash',
          subtitle: 'Video Game',
          date: '2025',
          description: 'Help the toy robot get back to where it belongs. Made with Unity 3D. Group Project for DIG3878',
          tags: ['Unity', 'Blender', 'C#', 'Github'],
          icon: '/icons/github.svg',
          link: 'https://github.com/Viscerus/3878_GroupProject'
        },
        {
          title: 'NeuroStock',
          subtitle: 'Web',
          date: '2024',
          description: 'Stock prediction ML model using historical Yahoo Finance Data. Group Project with Brian Loc Dinh and Jereme Yang',
          tags: ['Python', 'Flask', 'Sci-Kit Learn', 'Machine Learning', 'TensorFlow'],
          icon: '/icons/github.svg',
          link: 'https://github.com/LocBDinh/NeuroStock-Forecast'
        },
      ],
      education: [
        {
          title: 'Computer Science, B.S.',
          company: 'University of Florida',
          date: '2021 - 2025',
          description: 'Built my foundation of computer science theoritically and practically with a focus on software engineering'
        },
        {
          title: 'Digital Arts & Sciences Minor',
          company: 'University of Florida',
          date: '2024 - 2025',
          description: 'Focused on game developement using Unity and collaborating with fellow artists and programmers'
        }
      ],
      featuredApps: [
        {
          name: 'LiftNotes',
          description: 'Track your gym progress and make gains!',
          icon: '/app_icons/LiftNotes_logo.png',
          link: 'https://apps.apple.com/us/app/lift-notes-gym-tracker/id6753324391'
        },
        {
          name: 'Word O\' Mouth (JOIN THE BETA!)',
          description: 'Discover and review your favorite food spots!',
          icon: '/app_icons/WOM_logo.png',
          link: '/wom',
          external: false
        },
        {
          name: 'MoodJo',
          description: 'Log your mood along with a journal entry.',
          icon: '/app_icons/MoodJo_logo.png',
          link: 'https://apps.apple.com/us/app/moodjo-mood-journal/id6757492437'
        },
      ]
    }
  }
}
</script>
