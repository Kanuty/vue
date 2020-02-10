<template>
  <div class="wrapper">
    <transition name="slide">
      <img
        v-if="step === 1"
        src="../assets/vue_rock.svg"
        class="logo"
      >
    </transition>
    <transition name="fade">
      <Claim v-if="step === 0" />
    </transition>
    <div class="search">
      <SearchInput 
        v-model="searchValue" 
        @input="handleInput" 
      />
    </div>
    <div 
      v-if="results && loading && step === 1"
      class="results"
    >
      <Item 
        v-for="item in results"
        :item="item"
        :key="item.data[0].nasa_id"
      />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

import Claim from '@/components/Claim.vue';
import Item from '@/components/Item.vue'
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  components: {
    Claim,
    Item,
    SearchInput,
  },
   data() {
    return {
      results: [],
      searchValue: '',
      step: 0,
      loading: false,
    }
  }, 
  methods: {
    handleInput: debounce(function call() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items
          this.loading = true
          this.step = 1
        })
        .catch((error) => {
          console.log(error);
        });
    }, 650),
  },
};
</script>

<style lang="scss" scoped>
  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s ease;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

  .slide-enter-active, .slide-leave-active {
    transition: margin-top .5s ease;
  }
  .slide-enter, .slide-leave-to {
    margin-top: -170px;
  }

  .logo {
    height: 80px;
    position: absolute;
    top: -20px;
    width: 80px;
  }

  .wrapper {
    align-items: center;
    color: #42b983;
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 30px;
    position: relative;
    width: 100%;
    text-shadow: 1px 1px #14851d;
  }
</style>
