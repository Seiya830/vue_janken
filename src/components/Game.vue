<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'

export enum Hand { Guu = 0, Choki, Paa}
export type ActionPonType = (Hand: number) => void

export default defineComponent({
  props: {
    actionPon: {
      type: Function as PropType<ActionPonType>,
      required: true
    }
  },
  setup () {
    return { Hand }
  }
})
</script>

<template>
  <div>
    <button v-on:click="actionPon(Hand.Guu)">グー</button>
    <button v-on:click="actionPon(Hand.Choki)">チョキ</button>
    <button v-on:click="actionPon(Hand.Paa)">パー</button>
  </div>
</template>

<style>

</style>
