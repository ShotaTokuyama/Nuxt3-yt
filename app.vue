<script setup lang="ts">
import type { Character } from "@/types/interfaces";

const SITE_TITLE = "ワンピース";

useHead({
  title: SITE_TITLE,
  titleTemplate: (titleChunk: string | undefined): string => {
    return titleChunk != undefined ? `${titleChunk} | ${SITE_TITLE}` : SITE_TITLE;
  }
});

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
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<style scoped>
section {
  border: blue 5px solid;
  margin: 10px;
}
</style>