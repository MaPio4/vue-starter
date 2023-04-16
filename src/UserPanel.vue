<template>
  <div>
      <label>Jesteś zalogowany jako {{ email }}.</label>
      <button @click="logout()"> Wyloguj </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
    }
  },
  methods: {
    logout() {
      this.$emit('logout');
    },
  },
  props: {
    email: String,
  }
}
</script>
