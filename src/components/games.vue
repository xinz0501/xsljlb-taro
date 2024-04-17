<template>
  <view class="games">
    <template v-for="game in Games" :key="game.id">
      <view class="game">
        <AtAvatar circle :text="game.avatar" size="small"></AtAvatar>
        <text class="name">{{ game.name }}</text>
      </view>
    </template>
  </view>
</template>

<script setup>
import { AtAvatar } from "taro-ui-vue3";
import Games from "../mock/games";
</script>

<style lang="scss">
.games {
  display: grid;
  grid-template-columns: 20% 20% 20% 20% 20%;
  row-gap: 1rem;
  margin: 1rem 0;
  .game {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .name {
      font-size: 0.7rem;
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
    }
  }
}
</style>
