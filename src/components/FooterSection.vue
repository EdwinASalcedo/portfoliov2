<template>
  <footer class="footer">
    <div class="footer-content">
      <!-- <p class="footer-name">{{ name }}</p> -->
      <p class="footer-email">
        <a :href="`mailto:${email}`">{{ email }}</a>
      </p>
      <p class="footer-copyright">© {{ currentYear }} {{ name }}. All rights reserved.</p>
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

<style scoped>
.footer {
  background: var(--bg-secondary);
  padding: 40px 22px;
  text-align: center;
  border-top: 1px solid var(--border);
}

.footer-content {
  max-width: 980px;
  margin: 0 auto;
}

.footer-name {
  font-size: 17px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 8px;
}

.footer-email {
  font-size: 15px;
  margin-bottom: 12px;
}

.footer-email a {
  color: var(--accent);
  text-decoration: none;
  transition: opacity 0.3s ease;
}

.footer-email a:hover {
  opacity: 0.8;
}

.footer-copyright {
  font-size: 13px;
  color: var(--text-tertiary);
}
</style>
