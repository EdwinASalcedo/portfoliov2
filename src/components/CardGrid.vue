<template>
  <div class="grid grid-cols-[repeat(auto-fit,minmax(300px,1fr))] gap-6 mt-10 max-md:grid-cols-1">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="rounded-[18px] p-8"
      :class="'bg-white dark:bg-apple-raised'"
    >
      <div class="flex justify-between items-center gap-3 mb-2 mr-2">
        <h3 class="text-[24px] font-semibold tracking-[-0.01em] flex-1 text-neutral-900 dark:text-neutral-100">{{ item.title }}</h3>
        <div>
          <a
            v-if="showIcon && item.link"
            :href="item.link"
            target="_blank"
            rel="noopener noreferrer"
            class="opacity-60 flex items-center shrink-0 hover:opacity-100 hover:-translate-y-0.5"
            :aria-label="`Link to ${item.title}`"
          >
            <img v-if="item.icon" :src="item.icon" alt="Link icon" width="20" height="20" class="dark:invert dark:brightness-125" />
          </a>
        </div>
      </div>
      <p v-if="item.subtitle" class="text-[17px] text-neutral-900 dark:text-neutral-100 mb-1 font-normal">{{ item.subtitle }}</p>
      <p v-if="item.date" class="text-[14px] text-neutral-900 dark:text-neutral-100 mb-4">{{ item.date }}</p>
      <p class="text-[17px] leading-normal text-neutral-900 dark:text-neutral-100 whitespace-pre-line">{{ item.description }}</p>
      <div v-if="item.tags" class="flex flex-wrap gap-2 mt-4">
        <span
          v-for="tag in item.tags"
          :key="tag"
          class="bg-neutral-100 dark:bg-neutral-800 text-neutral-500 dark:text-neutral-300 px-3 py-1 rounded-xl text-[13px] font-normal"
        >{{ tag }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardGrid',
  props: {
    items: {
      type: Array,
      required: true
    },
    cardBg: {
      type: String,
      default: 'primary',
      validator: (value) => ['primary', 'secondary'].includes(value)
    },
    showIcon: {
      type: Boolean,
      default: false
    }
  }
}
</script>
