<template>
  <div id="app">
    <div class="navigation-buttons"> 
      <div class="is-pulled-right">
        <router-link to="/products" class="button">
          <i class="fa fa-user-circle mr-2"></i><span>Shop</span>
        </router-link>
        <router-link to="/cart" class="button is-primary">
          <i class="fa fa-shopping-cart mr-2"></i><span>{{ cartQuantity }}</span>
        </router-link>
        <button @click="logout" class="button is-text is-pulled-left">Logout</button>
      </div>
    </div>
    <div class="container">
      <div class="columns">
        <div class="column is-6 column--align-center m-auto">
          <router-view></router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  name: 'App',
  computed: {
    ...mapGetters([
      'cartQuantity'
    ]),
  },
  methods: {
    logout() {
      this.$store.dispatch("logout").then(() => {
        this.$router.push("/login")
      }).catch((error) => {
        console.log(error);
      });
    }
  },
  created() {
    const token = localStorage.getItem("token");
    if (token) {
      this.$store.dispatch('getCartItems', token);
      this.$store.dispatch('getProductItems', token);
    }
  },
  components: {
    
  }
}
</script>

<style>
html,
body {
  background: #f2f6fa;
}

#app {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media screen and (min-width: 769px) {
  html,
  body {
    height: 100%;
  }
}
</style>

