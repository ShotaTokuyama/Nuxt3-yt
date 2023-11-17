<script setup lang="ts">
import type { Character } from "@/types/interfaces";
const characterList = useState<Map<number, Character>>("characterList")

const totalBounty = computed((): number => {
  let total = 0;
  for (const character of characterList.value.values()) {
    total += character.bounty;
  }
  return total;
})
</script>

<template>
  <section>
    <h1>キャラクターリスト</h1>
    <p>懸賞金の合計：{{ totalBounty }}</p>
    <PropsSample v-for="id in characterList.keys()" :key="id" :id="id" />
  </section>
</template>