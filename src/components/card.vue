<template>
  <div class="card">
    <img class="card_back" src="../assets/card.jpg" alt="card">
    <img class="card_front" src="../assets/card_front.jpg" alt="card">
  </div>
</template>
<script>
export default {
  
}
</script>
<style lang="scss">
  .card {
    width: 150px;
    height: 200px;
    margin: 5px;
    position: relative;
    box-shadow: 1px 1px 1px rgba(0,0,0,.3);
  }
  .card_front, .card_back {
    position: absolute;
    width: 100%;
    height: 100%;
  }
</style>