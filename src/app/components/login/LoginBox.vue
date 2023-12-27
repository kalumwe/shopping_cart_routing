<template>
  <div id="login" class="box has-text-centered">
    <h2 class="title">Online Shop</h2>
     <button @click="login" class="button is-primary">Login</button>
  </div>
</template>

<script>
export default {
  name: 'LoginBox',
  methods: {
   login() {
    this.$store.dispatch("login").then(() => {
      this.$router.push({ path: '/products' });
    });
   }
 }
}
</script>

<style scoped>
.box {
    padding: 30px;
}
</style>