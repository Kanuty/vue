<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Search</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
* {
  box-sizing: border-box;
  font-family:'Courier New', Courier, monospace;
  margin: 0;
  padding: 0;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-image: url('./assets/background_mod.jpg');
  background-repeat: no-repeat;
  background-size: cover;
}

#nav {
  padding: 30px;

  a {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    font-weight: bold;
    color: #FDD835;

    &.router-link-exact-active {
      color: #42B983;
    }
  }
}
</style>
