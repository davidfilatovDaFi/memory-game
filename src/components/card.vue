<template>
  <div 
  @click="() => {
    this.$emit('active',Math.random())
    card.isMatched 
      || 
      card.isBlocked 
      || 
      card.isSelected ? card.isSelected = card.isSelected : card.isSelected = !card.isSelected
  }" 
  class="card" 
  :class="{flip: card.isSelected || card.isMatched}">
    <img class="card_front" :src="card.img" alt="card">
    <img class="card_back" src="../assets/card.jpg" alt="card">
  </div>
</template>
<script>
export default {
  props: {
    card: {type: Object}
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
    @media (max-width:680px) {
      width: 100px;
      height: 150px;
    }
    @media (max-width:510px) {
      width: 80px;
      height: 120px;
    }
    @media (max-width:370px) {
      width: 55px;
      height: 80px;
    }
  }
  .card_front, .card_back {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 15px;
    backface-visibility: hidden;
    transition: 1s;
    @media (max-width:680px) {
      border-radius: 8px;
    }
  }
  .card_front {
    transform: rotateY(180deg);
  }
  .flip {
    transform: rotateY(180deg);
  }
</style>