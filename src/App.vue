<script setup lang="ts">
import { defineComponent, reactive, ref, watch } from 'vue'
import { Game } from '@/components/Game.vue'
import { Score } from '@/components/Score.vue'

export default defineComponent({
  name: "app",
  setup() {
    scores: storage.getData('scores') || []
    watch(
      (): void => {
        scores: 'saveData'
      },
      {immediate: true}
    );
  }
})

</script>

<template>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <div>
    <h1>じゃんけんぽん！</h1>
    <game scores="scores"></game>
    <score scores="scores"></score>
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
