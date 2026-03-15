<template>
  <div class="max-w-245 mx-auto px-10 max-md:px-4">
    <!-- Clipping window -->
    <div class="relative overflow-hidden" ref="container">
      <!-- Track: moves via translateX -->
      <div
        class="flex gap-5"
        :style="{ transform: `translateX(${trackOffset}px)`, transition: 'transform 0.45s cubic-bezier(0.4,0,0.2,1)' }"
      >
        <div
          v-for="(item, index) in items"
          :key="index"
          class="shrink-0 rounded-[18px] p-8 bg-white dark:bg-apple-raised"
          :style="{ width: cardWidth + 'px' }"
        >
          <div class="flex justify-between items-center gap-3 mb-2">
            <h3 class="text-[22px] font-semibold tracking-[-0.01em] text-neutral-900 dark:text-neutral-100">{{ item.title }}</h3>
            <a
              v-if="item.link"
              :href="item.link"
              target="_blank"
              rel="noopener noreferrer"
              class="opacity-60 flex items-center shrink-0 hover:opacity-100"
              :aria-label="`Link to ${item.title}`"
            >
              <img v-if="item.icon" :src="item.icon" alt="Link icon" width="20" height="20" class="dark:invert dark:brightness-125" />
            </a>
          </div>
          <p v-if="item.subtitle" class="text-[15px] text-neutral-500 dark:text-neutral-400 mb-1">{{ item.subtitle }}</p>
          <p v-if="item.date" class="text-[13px] text-neutral-400 dark:text-neutral-500 mb-4">{{ item.date }}</p>
          <p class="text-[15px] leading-normal text-neutral-500 dark:text-neutral-400">{{ item.description }}</p>
          <div v-if="item.tags" class="flex flex-wrap gap-2 mt-4">
            <span
              v-for="tag in item.tags"
              :key="tag"
              class="bg-neutral-100 dark:bg-neutral-800 text-neutral-500 dark:text-neutral-300 px-3 py-1 rounded-xl text-[12px]"
            >{{ tag }}</span>
          </div>
        </div>
      </div>

      <!-- Right fade: desktop only, hidden when on last page -->
      <div
        v-if="visible > 1 && currentIndex < maxIndex"
        class="absolute inset-y-0 right-0 w-32 bg-linear-to-l from-apple-gray dark:from-apple-charcoal to-transparent pointer-events-none"
      ></div>
      <!-- Left fade: desktop only, visible once past index 0 -->
      <div
        v-if="visible > 1 && currentIndex > 0"
        class="absolute inset-y-0 left-0 w-32 bg-linear-to-r from-apple-gray dark:from-apple-charcoal to-transparent pointer-events-none"
      ></div>
    </div>

    <!-- Buttons + dots -->
    <div class="flex items-center justify-center gap-4 mt-8">
      <button
        @click="prev"
        :disabled="currentIndex === 0"
        class="w-9 h-9 rounded-full bg-neutral-200 dark:bg-neutral-700 flex items-center justify-center text-neutral-600 dark:text-neutral-300 disabled:opacity-30 hover:bg-neutral-300 dark:hover:bg-neutral-600 transition-colors cursor-pointer disabled:cursor-default text-lg"
        aria-label="Previous"
      >‹</button>

      <button
        @click="next"
        :disabled="currentIndex >= maxIndex"
        class="w-9 h-9 rounded-full bg-neutral-200 dark:bg-neutral-700 flex items-center justify-center text-neutral-600 dark:text-neutral-300 disabled:opacity-30 hover:bg-neutral-300 dark:hover:bg-neutral-600 transition-colors cursor-pointer disabled:cursor-default text-lg"
        aria-label="Next"
      >›</button>
    </div>
  </div>
</template>

<script>
const GAP = 20

export default {
  name: 'ProjectCarousel',
  props: {
    items: { type: Array, required: true }
  },
  data() {
    return {
      currentIndex: 0,
      cardWidth: 300,
      visible: 3
    }
  },
  computed: {
    trackOffset() {
      return -this.currentIndex * (this.cardWidth + GAP)
    },
    maxIndex() {
      return Math.max(0, this.items.length - this.visible)
    }
  },
  mounted() {
    this.$nextTick(() => requestAnimationFrame(() => this.updateDimensions()))
    window.addEventListener('resize', this.updateDimensions)
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.updateDimensions)
  },
  methods: {
    updateDimensions() {
      const w = this.$refs.container?.offsetWidth ?? 0
      this.visible = w < 768 ? 1 : 3
      this.currentIndex = Math.min(this.currentIndex, this.maxIndex)
      this.cardWidth = (w - GAP * (this.visible - 1)) / this.visible
    },
    prev() {
      this.currentIndex = Math.max(0, this.currentIndex - 1)
    },
    next() {
      this.currentIndex = Math.min(this.maxIndex, this.currentIndex + 1)
    }
  }
}
</script>
