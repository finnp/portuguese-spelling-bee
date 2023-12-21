<script setup lang="ts">
const email = "conor.sheehan.dev@gmail.com";
</script>

<template>
  <div class="info-dialog">
    <h3>{{ $t("helpCreateWords") }}</h3>

    <ul>
      <li>{{ $t("helpWordRule1") }}.</li>
      <li>{{ $t("helpWordRule2") }}.</li>
      <li>{{ $t("helpWordRule3") }}.</li>
    </ul>

    <h3>{{ $t("helpScorePoints") }}</h3>

    <ul>
      <li>{{ $t("helpPointsRule1") }}.</li>
      <li>{{ $t("helpPointsRule2") }}.</li>
      <li>{{ $t("helpPointsRule3A") }}. {{ $t("helpPointsRule3B") }}!</li>
    </ul>

    <h3>{{ $t("AboutGame") }}</h3>
    <ul>
      <li>
        {{ $t("AboutGameText") }}
      </li>
      <li>Feito para Carminho, que tenta sempre usar palavras portuguesas no "Spelling Bee".
      </li>
      <li>Originalmente criado por e bifurcado de
      <el-link
        type="primary"
        href="https://github.com/ConorSheehan1/spelling-bee"
        target="_blank">
        Open Source GitHub de ConorSheehan1
      </el-link>
      </li>
      <li>
        {{ $t("InspirationSpellingBee") }}
        <el-link
          type="primary"
          href="https://www.nytimes.com/puzzles/spelling-bee"
          target="_blank">
          New York Times Spelling Bee
        </el-link>
      </li>
      <li>
        {{ $t("WordlistSource") }}
        <el-link
          type="primary"
          href="https://natura.di.uminho.pt/download/sources/Dictionaries/wordlists/"
          target="_blank">
          Dicionários Natura
        </el-link>
      </li>
    </ul>

    <h3>{{ $t("Bugs") }}</h3>
    <ul>
      <li>
        {{ $t("BugText") }}
        <el-link
          type="primary"
          href="https://github.com/finnp/spelling-bee/issues"
          target="_blank"
          >GitHub</el-link
        >
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
.info-dialog {
  text-align: left;
}
</style>
