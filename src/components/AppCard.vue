<template>
  <div class="flex flex-col items-center text-center gap-4 p-8 rounded-[20px] bg-white dark:bg-apple-raised h-full">
    <img :src="icon" :alt="title" class="w-24 h-24 rounded-[22px] shrink-0" />
    <div class="flex flex-col gap-1 flex-1">
      <h4 class="text-[17px] font-semibold tracking-[-0.01em] text-neutral-900 dark:text-neutral-100">{{ title }}</h4>
      <p class="text-[14px] text-neutral-900 dark:text-neutral-100 leading-snug">{{ subtitle }}</p>
    </div>
    <button
      class="px-5 py-1.5 bg-accent text-white rounded-full text-[14px] font-semibold cursor-pointer hover:bg-accent-hover"
      @click="handleClick"
    >View</button>
  </div>
</template>

<script>
export default {
  name: 'AppCard',
  props: {
    icon: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      required: true,
    },
    to: {
      type: String,
      required: false,
    },
    external: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleClick() {
      if (this.external) {
        window.open(this.to, '_blank')
      } else if (this.to) {
        this.$router.push(this.to)
      }
    },
  },
}
</script>
