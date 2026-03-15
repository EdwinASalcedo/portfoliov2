<template>
  <footer class="bg-apple-gray dark:bg-apple-raised py-10 px-5.5 text-center">
    <div class="max-w-245 mx-auto">
      <p class="text-[15px] mb-3">
        <a :href="`mailto:${email}`" class="text-accent no-underline hover:opacity-80">{{ email }}</a>
      </p>
      <p class="text-[13px] text-neutral-500 dark:text-neutral-600">© {{ currentYear }} {{ name }}. All rights reserved.</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterSection',
  props: {
    name: {
      type: String,
      required: true
    },
    email: {
      type: String,
      required: true
    }
  },
  computed: {
    currentYear() {
      return new Date().getFullYear()
    }
  }
}
</script>
