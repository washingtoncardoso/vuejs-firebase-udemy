<template>
  <v-app>
    <v-navigation-drawer v-model="menu" app temporary>
      <v-list>
        <v-list-tile @click="selecionar('home')">
          <v-list-tile-action>
            <v-icon>home</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="'Home'"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="selecionar('perfil')">
          <v-list-tile-action>
            <v-icon>account_circle</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="'Perfil'"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="selecionar('registro')">
          <v-list-tile-action>
            <v-icon>contact_mail</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="'Registro'"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="selecionar('login')">
          <v-list-tile-action>
            <v-icon>arrow_forward</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="'Login'"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="primary" dark app>
      <v-toolbar-side-icon @click="menu = !menu"></v-toolbar-side-icon>
      <v-toolbar-title @click="componentAtual = 'home'" class="headline logo">
        <span>{{ titulo }}</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <v-container fluid fill-height>
        <v-slide-y-transition  mode="out-in">
          <component :is="componentAtual"></component>
        </v-slide-y-transition>
      </v-container>
    </v-content>

    <v-footer color="primary" dark>
      <v-layout justify-center>
        <span>Curso Vue Firebase em Espanhol - Washington Cardoso</span>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
import Home from "@/views/Home.vue";
import Login from "@/views/usuario/Login.vue";
import Perfil from "@/views/usuario/Perfil.vue";
import Registro from "@/views/usuario/Registro.vue";

export default {
  components: { Home, Login, Perfil, Registro },
  name: "App",
  data() {
    return {
      titulo: "Super Opera",
      componentAtual: "home",
      menu: false
    };
  },
  methods: {
    selecionar(view) {
      this.componentAtual = view;
      this.menu = false;
    }
  }
};
</script>


<style>

@import url("https://fonts.googleapis.com/css?family=Great+Vibes");

 .logo {
    font-family: 'Great Vibes', cursive !important;
    cursor: pointer;
  }

</style>
