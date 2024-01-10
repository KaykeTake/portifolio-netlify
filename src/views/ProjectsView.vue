<template>
  <v-app-bar v-if="isMobile">
    <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    <v-app-bar-title>My Projects in Vue</v-app-bar-title>
  </v-app-bar>
  <v-navigation-drawer v-model="drawer" :width="300">
    <v-list-item title="My Projects in Vue" subtitle="Are simplify projects"></v-list-item>
    <v-divider></v-divider>
    <v-list-item link title="TodoList" @click="changeProjects('todolist')"></v-list-item>
    <v-list-item link title="TicketShop" @click="changeProjects('ticketshop')"></v-list-item>
    <v-list-item link title="LoginScreen" @click="changeProjects('loginscreen')"></v-list-item>
    <template v-slot:append>
      <div class="pa-2">
        <v-btn block color="primary" to="/">Go to HomePage</v-btn>
      </div>
    </template>
  </v-navigation-drawer>
  <TodoList v-if="show === 'todolist'" />
  <TicketShop v-if="show === 'ticketshop'" />
  <LoginScreen v-if="show === 'loginscreen'" />
</template>
<script>
import TodoList from '../components/TodoList.vue'
import TicketShop from '../components/TicketShop.vue'
import LoginScreen from '../components/LoginScreen.vue'
export default {
  components: {
    TodoList,
    TicketShop,
    LoginScreen
  },
  data: () => ({
    show: 'todolist',
    drawer: false,
    isMobile: null
  }),
  methods: {
    changeProjects(project) {
      this.show = project
    },
    checkMobile() {
      this.isMobile = window.innerWidth <= 600 // ou outro valor de largura que você considere como "móvel"
    },
  },
  mounted() {
    this.checkMobile()
    window.addEventListener('resize', this.checkMobile)
  },
}
</script>
<style scoped></style>

<!-- <v-app-bar app v-if="isMobile">
  <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
  <v-app-bar-title>My Projects in Vue</v-app-bar-title>
  </v-app-bar>
  toggleDrawer() {
    this.drawer = !this.drawer
  },
  checkMobile() {
    this.isMobile = window.innerWidth <= 600 // ou outro valor de largura que você considere como "móvel"
  },
},
mounted() {
  this.checkMobile()
  window.addEventListener('resize', this.checkMobile)
},
} -->