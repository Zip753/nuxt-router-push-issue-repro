<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        {{ title }}
      </h1>
      <h2 class="subtitle">
        nuxt/nuxt.js#2737 reproduction
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green">Documentation</a>
        <a
          class="button--grey clickable"
          @click="updateRouteParams">Break the app</a>
      </div>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'

export default {
  components: {
    AppLogo
  },
  watchQuery: ['title'],
  async asyncData ({ query }) {
    console.log('[asyncData] query: ', query)
    const title = query.title || 'nuxt-router-push-issue-repro'
    console.log('[asyncData] title: ', title)
    return { title }
  },
  methods: {
    updateRouteParams () {
      console.log('[updateRouteParams] Pushing the route')
      this.$router.push({ name: 'index', query: { title: 'New title!' } })
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.clickable {
  cursor: pointer;
}
</style>
