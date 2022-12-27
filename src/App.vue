<script lang="ts">
import { defineComponent, reactive } from 'vue'
import type { ActionPonType, Hand } from '@/components/Game.vue'
import type { ScoreType, Judgment } from '@/components/Score.vue'
import Game from '@/components/Game.vue'
import Score from '@/components/Score.vue'

// 配列の型を定義
type State = {
  scores: ScoreType[];
}
// コンポーネントの処理内容を定義
export default defineComponent({
  name: 'Jyanken',
// コンポーネント登録
  components: {
    Game, Score
  },
  setup() {
    // リアクティブな変数を用意
    const state = reactive<State>({ scores: [] })
    //　じゃんけんの手の定義
    const pon: ActionPonType = (human: Hand) => {
      // 小数点以下切り捨てのランダムな数値を定義
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
  <div>
    <h1>じゃんけんぽん！</h1>
    <Game v-bind:actionPon="pon"></Game>
    <Score v-bind:scores="state.scores"></Score>
  </div>
</template>

<style scoped>
</style>
