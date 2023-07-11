<template>
  <div 
  @click="() => isActive = !isActive" 
  class="card" 
  :class="{flip: isActive}">
    <img class="card_front" src="../assets/card_front.jpg" alt="card">
    <img class="card_back" src="../assets/card.jpg" alt="card">
  </div>
</template>
<script>
export default {
  data() {
    return {
      isActive: false
    }
  }
}

</script>
<style lang="scss">
  .card {
    width: 150px;
    height: 200px;
    margin: 5px;
    position: relative;
    transform-style: preserve-3d;
    transition: 1s;
  }
  .card_front, .card_back {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 15px;
    backface-visibility: hidden;
    transition: 1s;
  }
  .card_front {
    transform: rotateY(180deg);
  }
  .flip {
    transform: rotateY(180deg);
  }
</style>