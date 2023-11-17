<script setup lang="ts">
import type { Character } from "@/types/interfaces";

const SITE_TITLE = "キャラクター詳細情報";

useHead({
  title: SITE_TITLE,
})

definePageMeta({
  layout: "character"
});

const route = useRoute();

//  キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList")
// キャラクターリストから該当キャラクターを取得
const character = computed((): Character => {
  const id = Number(route.params.id);
  return characterList.value.get(id) as Character;
})
</script>

<template>
  <nav id="breadcrumbs">
    <ul>
      <li>
        <NuxtLink :to="{ name: 'index' }">TOP</NuxtLink>
      </li>
      <li>
        <NuxtLink :to="{ name: 'character-characterList' }">キャラクターリスト</NuxtLink>
      </li>
      <li>{{ SITE_TITLE }}</li>
    </ul>
  </nav>
  <section>
    <h2>{{ SITE_TITLE }}</h2>
    <table>
      <tr>
        <td>No:</td>
        <td>{{ character.id }}</td>
      </tr>
      <tr>
        <td>名前:</td>
        <td>{{ character.name }}</td>
      </tr>
      <tr>
        <td>懸賞金:</td>
        <td>{{ character.bounty }}berry</td>
      </tr>
    </table>
  </section>
</template>