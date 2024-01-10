<template>
  <div class="home">
    <CardProfile />
  </div>
</template>

<script>
// @ is an alias to /src
import CardProfile from '../components/CardProfile.vue'

export default {
  name: 'HomeView',
  components: {
    CardProfile,
  },
}
</script>
