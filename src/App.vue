<template>
<section class="game">
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
  <card/>
</section>
</template>

<script>
import card from '@/components/card.vue'

export default {
  name: 'App',
  components: {
    card
  }
}
</script>

<style lang="scss">
  * {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  }
  body {
    background-color: #ffe7d0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .game {
    width: 850px;
    display: flex;
    flex-wrap: wrap;
  }
</style>
