<template>
  <div class="Vlt-template Vlt-bg-grey-lighter">
    <DemoBar v-if="isDemo" :link="demoLink" />
    <Header />
    <Nuxt />
    <Footer />
  </div>
</template>

<script>
export default {
  head() {
    if (process.client) {
      this.log(
        `%c${this.$t('layout_default_careers_title')}`,
        'font-family: Gill Sans, sans-serif; font-size: 40px; color: #dd0d00'
      )
      this.log(
        `%c${this.$t('layout_default_careers_body')}`,
        'font-family: Gill Sans, sans-serif; font-size: 16px;'
      )
      this.log(
        `%c${this.$t('layout_default_careers_link')}`,
        'font-family: Gill Sans, sans-serif;'
      )
    }

    return {
      script: [
        {
          src: 'https://identity.netlify.com/v1/netlify-identity-widget.js',
          defer: true,
        },
      ],
    }
  },

  computed: {
    isDemo() {
      return process.env.demo !== null
    },

    demoLink() {
      return process.env.demo
    },
  },

  methods: {
    log(txt, format) {
      console.log(txt, format) // eslint-disable-line no-console
    },
  },
}
</script>
