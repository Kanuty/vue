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
      <div
        class="close"
        @click="$emit('closeModal')" 
      />
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
@import 'src/variables/colors';
  .description {
    color: $universalDark;
  }

  .close {
    cursor: pointer;
    height: 50px;
    position: absolute;
    right: 0;
    top: 0;
    width: 50px;

    &::after,
    &::before
     {
      background: $universalDark;
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
      height: auto;
      width: 100%;
    }

    img {
      border:  2px ridge $secondary;
      box-shadow: 0px 0px 15px $universalDark;
      height: 350px;
      width: 350px;
    }
  }

  .outerWrapper {
    background: rgba(236, 238, 216, 0.95);
    border-radius: 5px;
    left: 0;
    max-width: 100%;
    position: fixed;
    top: 0;

    @media (min-width: 1024px) {
      bottom: 0;
      box-shadow: 5px 5px 50px $primary-shadow;
      height: 60%;
      left: 0;
      margin: auto;
      max-width: 70%;
      right: 0;
      top: 0;
    }
  }

</style>
