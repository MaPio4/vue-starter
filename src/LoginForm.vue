<template>
  <div>
      <label>Zaloguj się e-mailem</label>
      <input type="email" v-model="email">
      <button @click="enter()">Zaloguj się</button>
      <div>{{ errorMsg }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      errorMsg: '',
    }
  },
  methods: {
    enter() {
      if(this.validateMail(this.email))
        this.$emit('login', this.email);
    },
    validateMail(mail) {
      if(mail.length < 6) {
        this.errorMsg = `Email o długości ${mail.length} to zbyt krótki mail.`;
        return false;
      }
      else if(mail.length > 30) {
        this.errorMsg = `Email o długości ${mail.length} to zbyt długi mail.`;
        return false;
      }
      else if(!mail.includes('@')) {
        this.errorMsg = `Email nie posiada znaku @`;
        return false;
      }
      else {
        this.errorMsg = "";
        return true;
      }
    },
  }
}
</script>
