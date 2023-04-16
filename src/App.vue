<template>
  <div class="my-app">

    <h1>Witaj w systemie do zapisu na zajęcia!</h1>

    <div v-bind:hidden="loggedIn">Zaloguj się mailem:</div>
    <input v-bind:hidden="loggedIn" type="email" v-model="email" :on-change="validateMail()">
    <button v-bind:hidden="loggedIn" @click="login()"> Zaloguj</button>
    <div v-bind:hidden="loggedIn">{{ errorMsg }}</div>

    <h2 v-bind:hidden="!loggedIn">Witaj {{ email }}</h2>
    <div v-bind:hidden="!loggedIn" @click="logout()">Wyloguj</div>
  </div>
</template>

<script>
import "milligram";
export default {
  data() {
    return {
      email: '',
      password: '',
      loggedIn: false,
      errorMsg: '',
    };
  },
  methods: {
  alertMyEmail() {
    alert(this.email);
  },
  validateMail() {
    if(this.email.length == 0) {
      this.errorMsg = ``;
      return false;
    }
    if(this.email.length < 6) {
      this.errorMsg = `Email o długości ${this.email.length} to zbyt krótki mail.`;
      return false;
    }
    else if(this.email.length > 30) {
      this.errorMsg = `Email o długości ${this.email.length} to zbyt długi mail.`;
      return false;
    }
    else if(!this.email.includes('@')) {
      this.errorMsg = `Email nie posiada znaku @`;
      return false;
    }
    else {
      this.errorMsg = "";
      return true;
    }
  },
  login() {
    this.loggedIn = this.validateMail();
  },
  logout() {
    this.loggedIn = false;
  },
}
}
</script>

<style>
.my-app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
}
</style>
