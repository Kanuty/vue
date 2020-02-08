<template>
<div class="searchInputWrapper">
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
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'SearchInput',
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

<style scoped>
  .searchInputWrapper {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 0;
      padding: 30px;
      width: 100%;
    }
   .search {
    display: flex;
    flex-direction: column;
    width: 250px;
   }
    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid #DDD;
      color: #FDD835;
      text-shadow: 1px 1px #BB7711;
      background-color: rgba(0, 0, 0, 0.1);
      margin: 5px;
      padding: 0 0 0 5px;
    }
</style>
