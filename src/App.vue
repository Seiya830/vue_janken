<script setup lang="ts">
import { defineComponent, reactive } from 'vue'
import Game, { ActionPonType, Te } from './components/Game.vue'
import Score, { ScoreType, Judgment } from './components/Score.vue'
// import { ref } from 'vue';

type State = {
  scores: ScoreType[];
}

  export default defineComponent({
    name: 'Jyanken',
    components: {
      Game, Score
    },
    setup () {
      const state = reactive<State>({ scores: [] })
      const pon: ActionPonType = (human: Te) => {
        const computer: Te = Math.floor(Math.random() * 3)
      }
    }
  })


// const name = ref('田中太郎');
</script>

<template>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <h1>こんにちは！{{ name }}さん！！！！！</h1>
  <div>
    <h1>じゃんけんぽん！</h1>
    <Game v-bind:actionPon="pon"></Game>
    <Score v-bind:scores="state.scores"></Score>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
