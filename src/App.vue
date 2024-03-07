<template>
  <v-app id="inspire">
    <v-navigation-drawer
        class="navDrawer"
        v-model="drawer"
        app
        color="grey-lighten-2"
      >
        <v-list>
          <v-list-item prepend-icon="mdi-format-list-checks" title="Todo" to='/'></v-list-item>
          <v-list-item to="/about" prepend-icon="mdi-account-box" title="About"></v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-app-bar
        color="primary"
        image="https://picsum.photos/1920/1080?random"
        prominent
      >
        <template v-slot:image>
          <v-img
            gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <template v-slot:prepend>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        </template>

        <v-app-bar-title>To Do</v-app-bar-title>

        <v-spacer></v-spacer>

      </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const drawer = ref(false)
</script>

<script>
  export default {
    data: () => ({ drawer: null }),
  }
</script>

<style>
.navDrawer{
  background: #555;
}
</style>