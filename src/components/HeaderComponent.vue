<template>
 <div class="header" :style="{ backgroundColor: headerBackgroundColor }">
    <div class="left">
      <img src="@/assets/logo.png" alt="Logo" class="logo" />
    </div>
    <div class="right">
      <div v-if="loggedIn" class="user-info">
        <div class="avatar" :style="{ backgroundColor: avatarColor }">
          {{ user.name[0] }}{{ user.surname[0] }}
        </div>
        <div class="user-name">{{ full_name }}</div>
      </div>
      <button @click="toggleLoginStatus" class="login-button">
        {{ loggedIn ? "LOGOUT" : "LOGIN" }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["loggedIn"],
  data() {
    return {
      user: {
        name: "Emīls",
        surname: "Konrāds",
        code: "IT18013",
      },
      avatarColor: getRandomColor(),
      headerBackgroundColor: "#8505c0", 
    };
  },
  computed: {
    full_name() {
      return `${this.user.name} ${this.user.surname}`;
    },
  },
  methods: {
    toggleLoginStatus() {
      if (this.loggedIn) {
        if (window.confirm("Do you want to log out?")) {
          this.headerBackgroundColor = "#8505c0"; 
          this.$emit("logout");
        }
      } else {
        if (window.confirm("Do you want to log in?")) {
          this.headerBackgroundColor = "#8888c0"; 
          this.$emit("login");
        }
      }
    },
  },
};

function getRandomColor() {
  const letters = "0123456789ABCDEF";
  let color = "#";
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #fff;
  padding: 10px;
}

.right {
  display: flex;
  align-items: center;
  margin-left: auto;
}

.logo {
  width: 50px;
  height: 50px;
  margin-right: 10px;
}

.user-info {
  display: flex;
  align-items: center;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
  font-size: 20px;
}

.user-name {
  margin-left: 10px;
  font-weight: bold;
}

.login-button {
  background-color: #450c66;
  color: #fff;
  border: none;
  padding: 10px 15px;
  cursor: pointer;
  font-weight: bold;
}

.login-button:focus {
  outline: none;
}
</style>