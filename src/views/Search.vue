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
      v-if="step === 1 && results.length === 0"
      class="notFound"
    >
      <h3>There is no data about {{ searchValue }}</h3>
      <h4>Impossible! Maybe archives are not completed?</h4>
    </div>
    <div 
      v-if="results && loading && step === 1"
      class="results"
    >
      <Item 
        v-for="item in results"
        :key="item.data[0].nasa_id"
        :item="item"
        @click.native="handleModalOpen(item)"
      />
    </div>
    <transition name="fade">
      <Modal 
        v-if="modalOpen === true"
        :item="modalItem"
        @closeModal="modalOpen = false"
      />
    </transition>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

import Claim from '@/components/Claim.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Search',
  components: {
    Claim,
    Item,
    Modal,
    SearchInput,
  },
   data() {
    return {
      loading: false,
      modalItem: null,
      modalOpen: false,
      results: [],
      searchValue: '',
      step: 0,
    }
  }, 
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
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
  @import 'src/variables/colors';

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
    color: $primary;
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 30px;
    position: relative;
    width: 100%;
    text-shadow: 1px 1px $primary-shadow;
  }

  .results {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 20px;
    margin-top: 50px;
  }

</style>
