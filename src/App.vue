<template>
  <v-app>
    <v-main>
      <CardProfile />
      <v-divider></v-divider>
      <div :style="{'display': 'flex', 'justifyContent': 'center', 'font-size': 'xxx-large'}">
        PROJETOS PARA PORTIFÓLIO
      </div>
      <v-divider :style="{'margin-bottom': '50px'}"></v-divider>
      <TodoList/>
      <v-divider :style="{'margin-bottom': '50px', 'margin-top': '50px'}"></v-divider>
      <TicketShop/>
    </v-main>
  </v-app>
</template>

<script>
import CardProfile from './components/CardProfile.vue'
import TodoList from './components/TodoList.vue'
import TicketShop from './components/TicketShop.vue'
export default {
  name: 'App',

  components: {
    CardProfile,
    TodoList,
    TicketShop
  },

  data: () => ({
    //
  }),
}
</script>
<style scoped>

</style>
