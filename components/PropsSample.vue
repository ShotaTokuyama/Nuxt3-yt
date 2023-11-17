<script setup lang="ts">
import type { Character } from "@/types/interfaces";
// 1.子でPropsの準備
// 親から受け取るプロパティはdefineProps()で型宣言する
// Props interface(プロパティ・型)の定義
interface Props {
  id: number;
}

// definePropsを実行しPropsオブジェクトの設定。
const props = defineProps<Props>();

//  キャラクターリストをステートから取得
const characterList = useState<Map<number, Character>>("characterList")

// 該当するキャラを取得
const character = characterList.value.get(props.id) as Character;

// UPボタンをクリックしたときのメソッド
const bountyUp = (): void => {
  character.bounty += 1000;
}
</script>
<template>
  <section class="box">
    <p>{{ character.name }}</p>
    <p>懸賞金：{{ character.bounty }}ベリー</p>
    <button v-on:click="bountyUp">UP</button>
  </section>
</template>

<style scoped>
.box {
  border: black 5px solid;
  margin: 3px;
  padding: 10px;
}
</style>