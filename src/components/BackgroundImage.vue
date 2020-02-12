<template>
  <img class="backgroundImage">
</template>

<script>
export default {
  name: 'BackgroundImage',
};
</script>

<style lang='scss' scoped>
.backgroundImage{
  background-image: url('../assets/background_mod.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  height: 101%;
  left: -1px;
  position: fixed;
  top: -1px;
  width: 101%;
  z-index: -1;
}
</style>