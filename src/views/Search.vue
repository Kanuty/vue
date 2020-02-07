<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input
        id="search"
        name="search"
        v-model="searchValue"
        @input="handleInput"
      />
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{ item.data[0].description }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'search',
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function call() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          console.log(response.data.collection.items);
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 800),
  },
};
</script>
<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
    padding: 30px;
    width: 100%
  }

  .search {
    display: flex;
    flex-direction: column;
    width: 250px;
  label {
    font-family:'Courier New', Courier, monospace;
  }
    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
      font-family:'Courier New', Courier, monospace;
      padding: 0 0 0 5px;
    }
  }
</style>
