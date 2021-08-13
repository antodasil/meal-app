<template>
  <v-app>
    <v-app-bar app>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<style lang="scss">
.v-app-bar {
  padding: 0 25px;

  a {
    font-weight: bold;
    color: #2c3e50;
    text-decoration: none;
    margin: 0 5px;

    &.router-link-exact-active {
      color: #1697f6;
    }
  }
}
</style>
