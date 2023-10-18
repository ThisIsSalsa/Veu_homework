<template>
  <div class="navigation">
    <button @click="showHome" :class="{ active: activeTab === 'home' }">HOME</button>
    <button @click="showAbout" :class="{ active: activeTab === 'about' }">ABOUT ME</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeTab: "home",
    };
  },
  props: ["loggedIn"],
  methods: {
    showHome() {
      this.activeTab = "home";
      this.$emit("toggleComponent", "HomeComponent");
    },
    showAbout() {
      this.activeTab = "about";
      this.$emit("toggleComponent", "AboutMeComponent");
    },
  },
};
</script>

<style scoped>
.navigation {
  display: flex;
  flex-direction: column;
  background-color: #30024b;
  color: #fff;
  padding: 20px;
}

button {
  border: none;
  background: none;
  color: #fff;
  background-color: #640a7a;
  font-size: 16px;
  margin: 10px 0;
  cursor: pointer;
  transition: color 0.3s;
}

button.active {
  color: #c01229;
}

button:focus {
  outline: none;
}
</style>
