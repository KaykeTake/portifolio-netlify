<template>
  <v-app>
    <v-main>
      <CardProfile />
      <v-divider></v-divider>
      <div :style="{'display': 'flex', 'justifyContent': 'center', 'font-size': 'xxx-large', 'text-align':'center'}">
        PROJETOS PARA PORTIFÓLIO
      </div>
      <v-divider :style="{'margin-bottom': '50px'}"></v-divider>
      <TodoList/>
      <v-divider :style="{'margin-bottom': '50px', 'margin-top': '50px'}"></v-divider>
      <TicketShop/>
      <v-divider :style="{'margin-bottom': '50px', 'margin-top': '50px'}"></v-divider>
      <LoginScreen/>
    </v-main>
  </v-app>
</template>

<script>
import CardProfile from './components/CardProfile.vue'
import TodoList from './components/TodoList.vue'
import TicketShop from './components/TicketShop.vue'
import LoginScreen from './components/LoginScreen.vue'
export default {
  name: 'App',

  components: {
    CardProfile,
    TodoList,
    TicketShop,
    LoginScreen
  },

  data: () => ({
    //
  }),
}
</script>
<style scoped>

</style>
