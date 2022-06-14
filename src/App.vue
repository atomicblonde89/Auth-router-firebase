<template>
  <div id="app">
    <b-navbar toggleable="lg" type="danger" style="background: rgb(131,58,180);
    background: linear-gradient(249deg, rgba(131,58,180,1) 0%, rgba(48,253,29,1) 50%, rgba(0,0,0,1) 100%)">
      <b-img src="https://bootstrap-vue.org/_nuxt/icons/icon_512x512.67aef2.png" width="20px"></b-img>
      <b-navbar-brand href="#">Authentication+Router+Firebase</b-navbar-brand>
      <router-link class="ml-auto" to="/">Home</router-link> |
      <template v-if="!isloggedIn">
        <router-link  to="/login">Login</router-link>
      </template>
      <template v-else>
        <button @click="logout" class="btn btn-link">Logout</button>
      </template>
    </b-navbar>
    <router-view />
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";

export default {
  name: "App",
  computed: {
    ...mapState(["loggedIn"]),
    isloggedIn() {
      return this.loggedIn ? true : false;
    },
  },
  methods: {
    ...mapActions(["logout"]),
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>