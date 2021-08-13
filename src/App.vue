<template>
  <v-app :theme="theme">
    <v-app-bar app>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Vue } from "vue-property-decorator";
export default class App extends Vue {
  theme = "light";

  setTheme(e: MediaQueryList | MediaQueryListEvent): void {
    if (e.matches) {
      this.theme = "dark";
    } else {
      this.theme = "light";
    }
  }

  initTheme(): void {
    const darkThemeMq = window.matchMedia("(prefers-color-scheme: dark)");
    this.setTheme(darkThemeMq);

    const updateTheme = this.setTheme.bind(this);
    darkThemeMq.addEventListener("change", (e) => {
      updateTheme(e);
    });
  }

  created(): void {
    this.initTheme();
  }
}
</script>

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
