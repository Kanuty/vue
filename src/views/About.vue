<template>
  <div class="about">
    <h1>App made with help of this tutorial (lang - PL): </h1>
    <br>
    <a href="https://www.youtube.com/watch?v=A2rEhxkFPDw">https://www.youtube.com/watch?v=A2rEhxkFPDw</a>
    <br>
    <br>
    <h1>Git page: </h1>
    <br>
    <a href="https://github.com/Kanuty">https://github.com/Kanuty</a>
  </div>
</template>

<style lang="scss" scoped>
  @import 'src/variables/colors';

  .about {
    align-items: center;
    color: $primary ;
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 30px;
    width: 100%;
    text-shadow: 1px 1px $primary-shadow;
  }
  a {
    color: $secondary;
    text-shadow: 1px 1px $secondary-shadow;
  }
</style>
