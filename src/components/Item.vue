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
  .item {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
    box-shadow: 2px 2px 3px #333;
    height: 300px;
    width: 300px;
  }
</style>