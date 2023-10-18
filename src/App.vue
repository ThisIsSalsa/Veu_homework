<template>
  <div id="app">
    <HeaderComponent :loggedIn="loggedIn" @login="login" @logout="logout" />
    <div class="main-container">
      <NavigationComponent v-if="loggedIn" @toggleComponent="showComponent" />
      <div class="content">
        <component :is="activeComponent" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from "@/components/HeaderComponent.vue";
import NavigationComponent from "@/components/NavigationComponent.vue";
import HomeComponent from "@/components/HomeComponent.vue";
import AboutMeComponent from "@/components/AboutMeComponent.vue";

export default {
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent,
  },
  data() {
    return {
      loggedIn: false,
      activeComponent: null,
    };
  },
  methods: {
    login() {
      this.loggedIn = true;
      this.activeComponent = "HomeComponent";
    },
    logout() {
      this.loggedIn = false;
      this.activeComponent = null;
    },
    showComponent(component) {
      this.activeComponent = component;
    },
  },
};
</script>

<style>
#app {
  background-color: #210830;
}
.main-container {
  display: flex;
}

.content {
  flex: 1;
  padding: 220px;
}
</style>