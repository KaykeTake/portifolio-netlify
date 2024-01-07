<template>
  <v-app>
    <v-main>
      <CardProfile />
    </v-main>
  </v-app>
</template>

<script>
import CardProfile from './components/CardProfile.vue'

export default {
  name: 'App',

  components: {
    CardProfile,
  },

  data: () => ({
    //
  }),
}
</script>
