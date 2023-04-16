<template>
  <div class="my-app">

    <h1>Witaj w systemie do zapisu na zajęcia!</h1>

    <div v-if="email.length <= 0">
      <LoginForm @login="(username) => logMeIn(username)" buttonLabel="Zaloguj"></LoginForm>
    </div>

    <div v-else>
      Zalogowano jako {{ email }} <br>
      <button @click="logMeOut()">Wyloguj</button>
    </div>

  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
export default {
  data() {
    return {
      email: '',
    };
  },
  methods: {
    logMeIn(username) {
      this.email = username;
      console.log(`Logged in as ${username}`);
    },
    logMeOut() {
      this.email = "";
    },
  },
  components: {
    LoginForm,
  },
}
</script>

<style>
.my-app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
