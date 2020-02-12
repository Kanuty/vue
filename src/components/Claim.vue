<template>
  <div class="claimWrapper">
    <h1 class="claim">SPACER</h1>
    <p class="subclaim">
      Begin your journey through our amazing galaxy
      and discover planets you never even heard of.
    </p>
    <p class="subclaim">
      Type anything space-related ( Mars for example ) to start.
    </p>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
  .claimWrapper {
    align-items: center;
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: center;
    max-width: 70vw;
  }

  .claim {
    font-size: 70px;
    margin: 0;
  }

  .subclaim {
    font-size: 20px;
    margin: 20px 0 0 0;
  }

</style>
