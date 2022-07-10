<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
  <UserDashboard/>
  <!-- <router-view/> -->
</template>

<script>
import UserDashboard from '@/views/UserDashboard.vue'
export default {
  name: 'App',
  components: {
    UserDashboard
  }
  
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Rubik', Helvetica, Arial, sans-serif;
  font-weight: 300;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: $very-dark-blue;
  color: $white;
  min-height: 100vh;
  padding: 20px;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>