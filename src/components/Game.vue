<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'Game',
  setup() {
    //　勝敗の結果を表す変数を定義。初期値は空文字
    const result = ref('');
    //　コンピュータの手を表す変数を定義
    const computer = ref('');

    // コンピュータの手をランダムに決める
    function play(player: string) {
      const hands = ['グー', 'チョキ', 'パー'];
      computer.value = hands[Math.floor(Math.random() * hands.length)];

      // じゃんけんの勝敗を判定するロジック
      if (player === computer.value) {
        result.value = '引き分け';
      } else if (
        (player === 'グー' && computer.value === 'チョキ') ||
        (player === 'チョキ' && computer.value === 'パー') ||
        (player === 'パー' && computer.value === 'グー')
      ) {
        result.value = '勝ち';
      } else {
        result.value = '負け';
      }
    }

    return {
      result,
      computer,
      play,
    };
  },
});
</script>

<template>
  <div>
    <h1>じゃんけんゲーム</h1>
    <p class="text">相手： {{ computer }}</p>
    <p class="text">結果： {{ result }}</p>
    <div class="btn">
      <button @click="play('グー')">グー</button>
      <button @click="play('チョキ')">チョキ</button>
      <button @click="play('パー')">パー</button>
    </div>
  </div>
</template>

<style>
  h1, .text, .btn {
    text-align: center;
  }

  button {
    margin-right: 10px;
  }

  button:hover {
    cursor: pointer;
  }
</style>