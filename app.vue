<script setup lang="ts">
import type { Character } from "@/types/interfaces";

useState<Map<number, Character>>(
  // ステート名
  "characterList",
  // 初期値を生成
  (): Map<number, Character> => {
    const characterListInit = new Map<number, Character>();
    characterListInit.set(1, { id: 1, name: "ルフィ", bounty: 1000000 })
    characterListInit.set(2, { id: 2, name: "ゾロ", bounty: 600000 })
    return characterListInit;
  }
  // characterListでデータの取り出しが可能。
);
</script>
<template>
  <header>
    <h1>OnePiece</h1>
  </header>
  <main>
    <NuxtPage />
  </main>
</template>

<style scoped>
section {
  border: blue 5px solid;
  margin: 10px;
}
</style>