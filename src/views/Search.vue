<template>
  <div class="wrapper">
    <Claim />
    <div class="search">
     <SearchInput />
    </div>
  </div>
</template>

<script>


import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

export default {
  name: 'search',
  components: {
    Claim,
    SearchInput,
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
    width: 100%;
    color: #42b983 ;
    text-shadow: 1px 1px #14851D;
  }
</style>
