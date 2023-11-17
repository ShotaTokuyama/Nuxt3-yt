<script setup lang="ts">
import type { Character } from "@/types/interfaces";

//  キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList")
</script>

<template>
  <h1>TOP</h1>
  <nav id="breadcrumbs">
    <ul>
      <li>
        <NuxtLink :to="{ name: 'index' }">
          TOP
        </NuxtLink>
      </li>
      <li>キャラクターリスト</li>
    </ul>
  </nav>
  <section>
    <h2>キャラクターリスト</h2>
    <p>追加は<NuxtLink :to="{ name: 'character-characterAdd' }">こちら</NuxtLink>から</p>
    <ul>
      <li v-for="[id, character] in characterList" :key="id">
        <NuxtLink :to="{ name: 'character-characterDetail-id', params: { id: id } }">
          No:{{ id }} {{ character.name }}
        </NuxtLink>
      </li>
    </ul>
  </section>
</template>