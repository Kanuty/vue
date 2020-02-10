<template>
  <div id="app">
    <BackgroundImage />
    <div id="nav">
      <router-link to="/">Search</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>
<script>

import BackgroundImage from '@/components/BackgroundImage.vue';

export default {
   name: 'App',
  components: {
    BackgroundImage,
  },
}
</script>
<style lang="scss">
* {
  box-sizing: border-box;
  font-family:'Courier New', Courier, monospace;
  margin: 0;
  padding: 0;
}
#app {
  color: #2c3e50;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  text-align: center;
}

#nav {
  padding: 30px;

  a {
    color: #fdd835;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-weight: bold;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
