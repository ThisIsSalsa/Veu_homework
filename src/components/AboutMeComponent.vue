<template>
  <div class="about-me">
    <h1 style="color: white;">About Me</h1>
    <div class="user-info">
      <h3 style="color: white;">Name: {{ user.name }}</h3>
      <h3 style="color: white;">Surname: {{ user.surname }}</h3>
      <h3 style="color: white;">Code: {{ user.code }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "Emīls",
        surname: "Konrāds",
        code: "IT18013",
      },
    };
  },
};
</script>

<style scoped>
.about-me {
  text-align: center;
  padding: 20px;
}

.user-info {
  margin-top: 20px;
}

h1 {
  font-size: 24px;
  font-weight: bold;
}

h3 {
  font-size: 16px;
  margin: 10px 0;
}
</style>
