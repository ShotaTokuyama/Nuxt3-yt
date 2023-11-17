<script setup lang="ts">
import type { Character } from "@/types/interfaces";

// ルータオブジェクトを取得
const router = useRouter();

// キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList")

// 入力データと同期させるcharacterオブジェクトの用意
const character: Character = reactive({
  id: 0,
  name: "",
  bounty: 0,
})

// 登録ボタンが押された時の処理
const onAdd = (): void => {
  characterList.value.set(character.id, character);
  router.push({ name: "character-characterList" });
} 
</script>

<template>
  <h1>キャラクター設定</h1>
  <nav id="breadcrumbs">
    <ul>
      <li>
        <NuxtLink :to="{ name: 'index' }">TOP</NuxtLink>
      </li>
      <li>
        <NuxtLink :to="{ name: 'character-characterList' }">キャラクターリスト</NuxtLink>
      </li>
      <li>キャラクター追加</li>
    </ul>
  </nav>
  <section>
    <h2>キャラクター追加</h2>
    <p>情報を入力し、登録ボタンをクリックしてください。
    </p>
    <form v-on:submit.prevent="onAdd">
      <table>
        <tr>
          <td><label for="addId">No:</label></td>
          <td><input type="number" id="addId" v-model.number="character.id" required></td>
        </tr>
        <tr>
          <td><label for="addId">名前:</label></td>
          <td><input type="text" id="addId" v-model="character.name" required></td>
        </tr>
        <tr>
          <td><label for="addId">懸賞金:</label></td>
          <td><input type="number" id="addId" v-model.number="character.bounty" required></td>
        </tr>
      </table>
      <br>
      <button type="submit">登録</button>
    </form>
  </section>
</template>