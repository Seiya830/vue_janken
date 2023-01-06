<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'Game',
  setup() {
    const result = ref('');
    const computer = ref('');

    function play(player: string) {
       // コンピュータの手をランダムに決める
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
    <p>{{ result }}</p>
    <p>相手： {{ computer }}</p>
    <button @click="play('グー')">グー</button>
    <button @click="play('チョキ')">チョキ</button>
    <button @click="play('パー')">パー</button>
  </div>
</template>