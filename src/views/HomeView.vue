<template>
  <div class="home">
    <NewCard />
  </div>
</template>

<script>
// @ is an alias to /src
import NewCard from '../components/NewCard.vue'

export default {
  name: 'HomeView',
  components: {
    NewCard,
  },
}
</script>
