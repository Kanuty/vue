<template>
  <div class="searchInputWrapper">
    <label for="search">Search</label>
        <input
          id="search"
          name="search"
          :value="value"
          @input="handleChange"
        />
  </div>
</template>

<script>

export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
    data() {
      return {
        searchValue: '',
        results: [],
        loading: false,
        step: 0,
      };
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style scoped>
  .searchInputWrapper {
      align-items: center;
      display: flex;
      flex-direction: column;
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
      background-color: rgba(0, 0, 0, 0.1);
      border: 0;
      border-bottom: 1px solid #fdd835;
      color: #fdd835;
      height: 30px;
      margin: 5px;
      padding: 0 0 0 5px;
      text-shadow: 1px 1px #bb7711;
      text-align: center;
      transition: background-color .7s, box-shadow .2s;
    }

    input:focus {
      background-color: rgba(0, 0, 0, 0.3);
      box-shadow: 0px 2px 0px #bb7711;;
      outline:none;
    }
</style>
