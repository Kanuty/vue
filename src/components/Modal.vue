<template>
  <div class="outerWrapper">
    <div class="innerWrapper">
      <div class="photo">
        <img :src="photo">
      </div>
      <div class="description">
        <h2 class="title">{{ title }}</h2>
          <p class="description">
            {{ description }}
          </p>
        </div>
      </div>
      <div class="close" @click="$emit('closeModal')" />
    </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      description: null,
      photo: null,
      title: null,
    };
  },
  mounted() {
    this.description = this.item.data[0].description.substring(0,200);
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
  }
};
</script>

<style lang="scss" scoped>
  .description {
    color: #333;
  }

  .close {
    cursor: pointer;
    position: absolute;
    height: 50px;
    right: 0;
    top: 0;
    width: 50px;

    &::after,
    &::before
     {
      background: #333;
      content: '';
      display: block;
      height: 4px;
      position: absolute;
      right: 40px;
      top: 40px;
      width: 30px;
    }

    &::after {
      transform: rotate(-45deg);
    }

    &::before {
      transform: rotate(45deg);
    }
  }

  .innerWrapper {
    align-items: center;
    display: flex;
    height: 100%;
    justify-content: center;
    padding: 50px;

    @media (min-width: 1024px) {
      flex-direction: row;

      .photo {
        margin-right: 20px;
        min-width: 50px;
      }
    }

    .photo {
      background: #333;
      height: auto;
      width: 100%;
    }

    img {
      box-shadow: 5px 5px 3px #333;
      height: 350px;
      width: 350px;
    }
  }

  .outerWrapper {
    background: #ccc;
    left: 0;
    max-width: 100%;
    position: fixed;
    top: 0;

    @media (min-width: 1024px) {
      bottom: 0;
      box-shadow: 20px 30px 30px -10px rgba(28, 141, 13, 0.6);
      height: 60%;
      left: 0;
      margin: auto;
      max-width: 70%;
      right: 0;
      top: 0;
    }
  }

</style>
