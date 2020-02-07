<template>
<div class="searchInputWrapper">
   <label for="search">Search</label>
      <input
        id="search"
        name="search"
        v-model="searchValue"
        @input="handleInput"
      />
</div>
</template>

<script>
export default {
  name: 'SearchInput',
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
      border-bottom: 1px solid black;
      margin: 5px;
      padding: 0 0 0 5px;
    }
</style>
