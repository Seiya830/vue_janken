<script setup lang="ts">
import { defineComponent, reactive } from 'vue'
import Game, { ActionPonType, Hand } from '@/components/Game.vue'
import Score, { ScoreType, Judgment } from '@/components/Score.vue'

type State = {
  scores: ScoreType[];
}

export default defineComponent({
  name: 'Jyanken',
  components: {
    Game, Score
  },
  setup() {
    const state = reactive<State>({ scores: [] })
    const pon: ActionPonType = (human: Hand) => {
      const computer: Hand = Math.floor(Math.random() * 3)
      const judgment: Judgment = (computer - human + 3) % 3
      const score = { human: human, computer: computer, judgment: judgment }
      state.scores = [score, ...state.scores]
    }
    return { state, pon }
  }
})
</script>

<template>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <div>
    <h1>じゃんけんぽん！</h1>
    <Game v-bind:actionPon="pon"></Game>
    <Score v-bind:scores="state.scores"></Score>
  </div>
</template>

<style scoped>
</style>
