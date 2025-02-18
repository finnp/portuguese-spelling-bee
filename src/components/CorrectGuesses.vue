<script setup lang="ts">
import { computed, ref } from "vue";
import { useMainStore } from "../store";
import { gridify } from "../utils";

import { useI18n } from "vue-i18n";
import pt from "../locales/pt.json";

const { t } = useI18n({
  inheritLocale: true,
  messages: {
    pt,
  },
});

const store = useMainStore();
// showWords el-collapse has 2 elems when expanded, 1 when collapsed.
const showWords = ref([false]);
const numCorrectMessage = computed(() => {
  return t("foundWords", store.getCorrectGuesses.length);
});

const lastFiveGuesses = computed(() => {
  const numGuessesToShow = Math.min(store.getCorrectGuesses.length, 5);
  return store.getCorrectGuesses.reverse().slice(0, numGuessesToShow);
});

// alphabetical when expanded, in order found when collapsed.
const gridData = computed(
  () => gridify({ arr: Array.from(store.getCorrectGuesses).sort(), size: 3 })
  // gridify({ arr: Array.from(Array(100).keys()), size: 3 })
);
</script>

<template>
  <el-collapse
    v-model="showWords"
    @change="showWords.length == 2 ? $emit('open') : $emit('close')">
    <el-collapse-item>
      <template #title>
        <template v-if="showWords.length === 2">
          {{ numCorrectMessage }}
        </template>
        <template v-else-if="lastFiveGuesses.length === 0">
          {{ t("Your words") }}...
        </template>
        <template v-else>
          <span
            v-for="(guess, index) in lastFiveGuesses"
            :key="guess"
            :class="store.cellClassName({ row: [guess], columnIndex: -1 })">
            {{ guess }}{{ index === lastFiveGuesses.length - 1 ? "" : ", " }}
          </span>
          <span v-if="lastFiveGuesses.length === 5"> ... </span>
        </template>
      </template>
      <el-table
        :data="gridData"
        class="correct-guesses-table"
        :cell-class-name="store.cellClassName">
        <el-table-column property="1" label="" />
        <el-table-column property="2" label="" />
        <el-table-column property="3" label="" />
      </el-table>
    </el-collapse-item>
  </el-collapse>
</template>

<style scoped lang="scss">
@import "../assets/styles/_variables";

.correct-guesses-table {
  min-height: 50vh;
}

html.dark .el-collapse {
  background-color: $bl-el-plus-dark-bg;
}
</style>
