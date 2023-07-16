<template>
<section class="game">
  <card @active="setIsActive" v-for="card in cards" :key="card.id" :card="card"/>
</section>
</template>

<script>
import card from '@/components/card.vue'

export default {
  name: 'App',
  data() {
    return {
      cards: [
        {id: 1, number: 2, img: 'https://sun9-5.userapi.com/impf/c622124/v622124983/15a3a/Bscskf0lA0E.jpg?size=682x1024&quality=96&sign=af20c93c43c3f8dd9ed3c458bd3ef56f&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 2, number: 3, img: 'https://sun9-9.userapi.com/impf/c622124/v622124983/15a79/ygXHroNWP08.jpg?size=682x1024&quality=96&sign=4c3c7f186134dfa85903fbebfd4d2b9d&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 3, number: 4, img: 'https://sun9-4.userapi.com/impf/c622124/v622124983/15a9d/HRad-X7_QiY.jpg?size=682x1024&quality=96&sign=4d1ce0056ea2c925b0a7e57ed0219147&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 4, number: 5, img: 'https://sun9-33.userapi.com/impf/c622124/v622124983/15ab8/HRLTZDK4Fjw.jpg?size=682x1024&quality=96&sign=2ab37f7e8a7f548493fdd4d734db0cce&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 5, number: 6, img: 'https://sun9-67.userapi.com/impf/c622124/v622124983/15adc/WDjoUDr7jS0.jpg?size=682x1024&quality=96&sign=47e685d43eb166e0a76dd3f827faa0e9&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 6, number: 7, img: 'https://sun9-19.userapi.com/impf/c622124/v622124983/15b09/AKYVqsshtWw.jpg?size=682x1024&quality=96&sign=6165ca470edf565148739b01ea670dec&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 7, number: 2, img: 'https://sun9-5.userapi.com/impf/c622124/v622124983/15a3a/Bscskf0lA0E.jpg?size=682x1024&quality=96&sign=af20c93c43c3f8dd9ed3c458bd3ef56f&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 8, number: 3, img: 'https://sun9-9.userapi.com/impf/c622124/v622124983/15a79/ygXHroNWP08.jpg?size=682x1024&quality=96&sign=4c3c7f186134dfa85903fbebfd4d2b9d&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 9, number: 4, img: 'https://sun9-4.userapi.com/impf/c622124/v622124983/15a9d/HRad-X7_QiY.jpg?size=682x1024&quality=96&sign=4d1ce0056ea2c925b0a7e57ed0219147&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 10, number: 5, img: 'https://sun9-33.userapi.com/impf/c622124/v622124983/15ab8/HRLTZDK4Fjw.jpg?size=682x1024&quality=96&sign=2ab37f7e8a7f548493fdd4d734db0cce&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 11, number: 6, img: 'https://sun9-67.userapi.com/impf/c622124/v622124983/15adc/WDjoUDr7jS0.jpg?size=682x1024&quality=96&sign=47e685d43eb166e0a76dd3f827faa0e9&type=album', isSelected: false, isMathced: false, isBlocked: false},
        {id: 12, number: 7, img: 'https://sun9-19.userapi.com/impf/c622124/v622124983/15b09/AKYVqsshtWw.jpg?size=682x1024&quality=96&sign=6165ca470edf565148739b01ea670dec&type=album', isSelected: false, isMathced: false, isBlocked: false},
      ],
      isActive: false
    }
  },
  methods: {
    setIsActive(value) {
      this.isActive = value
    }
  },
  components: {
    card
  },
  mounted() {
    this.cards.sort((a,b) => Math.random(a) - Math.random(b))
  },
  watch: {
    isActive() {
      const selectedCards = this.cards.filter(card => card.isSelected === true && card.isMathced === false)

      if (selectedCards.length > 1) {
        if (selectedCards[0].number === selectedCards[1].number) {
          this.cards.forEach(card => {
          if (card.isSelected === true) card.isMathced = true
        }) 
        } else {
          this.cards.forEach(card => {
            card.isBlocked = true
          }) 
          setTimeout(() => {
            this.cards.forEach(card => {
              if (card.isMathced === false) card.isSelected = false
              card.isBlocked = false
            }) 
          }, 1000);
        }
      }

      if (this.cards.every(card => card.isMathced === true)) {
        setTimeout(() => {
          this.cards.forEach(card => {
            card.isMathced = false
            card.isSelected = false
          })
        },1000)
        setTimeout(() => {
          this.cards.sort((a,b) => Math.random(a) - Math.random(b))
        },1800)
      }
    }
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
    width: 650px;
    display: flex;
    flex-wrap: wrap;
  }
</style>
