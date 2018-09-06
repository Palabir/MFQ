<template>
  <v-app white>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-footer  app>
      <span>&copy; 2018</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        items: [
          { icon: 'apps', title: 'Welcome', to: '/' },
          { icon: 'bubble_chart', title: 'Inspire', to: '/inspire' }
        ],
        title: 'Vuetify.js'
      }
    }
  }
</script>
