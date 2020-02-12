<template>
  <div>
    <div :style="style" class="item" />
  </div>
</template>

<script>
  export default {
    name: "Item",
      props: {
        item: {
          type: Object,
          required: true,
      },
    },
    data() {
      return {
        photo: this.item.links[0].href,
        title: this.item.data[0].title,
      };
    },
    computed: {
      style() {
        return `background-image: url("${this.photo}")`;
      },
    },
  };
</script>

<style lang="scss" scoped>
  @import 'src/variables/colors';

  .item {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
    border:  2px ridge $secondary;
    box-shadow: 2px 2px 3px $universalDark;
    cursor: pointer;
    height: 300px;
    transition: 0.3s;
    width: 300px;

    &:hover {
      box-shadow: 0px 0px 15px $secondary-shadow;
    }
  }
</style>