<template>
  <view class="home-container">
    <view class="swiper-container">
      <swiper
        class="swiper"
        indicatorColor="#999"
        indicatorActiveColor="#333"
        :current="currentSwiper"
        :duration="duration"
        :interval="interval"
        :circular="isCircular"
        :autoplay="isAutoplay"
        :indicatorDots="hasIndicatorDots"
      >
        <swiper-item v-for="(item, idx) in imgUrls" :key="idx">
          <image :src="item" class="slide-image" />
        </swiper-item>
      </swiper>
    </view>
    <view class="games-avatar-grid">
      <template v-for="game in Games" :key="game.id">
        <view class="item">
          <AtAvatar circle :text="game.avatar" size="small"></AtAvatar>
          <text class="name">{{ game.name }}</text>
        </view>
      </template>
    </view>
    <view class="members-container">
      <text class="title">俱乐部大神</text>
      <view class="scroll-view-container">
        <Members></Members>
      </view>
    </view>
  </view>
</template>

<script setup>
import { ref } from "vue";
import Members from "../members/index.vue";
import { AtAvatar } from "taro-ui-vue3";
import Games from "../../mock/games";

const currentSwiper = ref(1);
const duration = ref(500);
const interval = ref(5000);
const isCircular = ref(true);
const isAutoplay = ref(true);
const hasIndicatorDots = ref(true);
const imgUrls = ref([
  "https://img10.360buyimg.com/babel/s700x360_jfs/t25855/203/725883724/96703/5a598a0f/5b7a22e1Nfd6ba344.jpg!q90!cc_350x180",
  "https://img11.360buyimg.com/babel/s700x360_jfs/t1/4776/39/2280/143162/5b9642a5E83bcda10/d93064343eb12276.jpg!q90!cc_350x180",
  "https://img14.360buyimg.com/babel/s700x360_jfs/t1/4099/12/2578/101668/5b971b4bE65ae279d/89dd1764797acfd9.jpg!q90!cc_350x180",
]);
</script>
<style lang="scss">
.home-container {
  .swiper-container {
    border-radius: 2%;
    overflow: hidden;
    height: 20vh;
    .swiper {
      height: 100%;
      .slide-image {
        width: 100%;
        height: 100%;
      }
    }
  }
  .games-avatar-grid {
    display: grid;
    grid-template-columns: 20% 20% 20% 20% 20%;
    row-gap: 1rem;
    margin: 1rem 0;
    .item {
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
  .members-container {
    .title {
      font-size: 1rem;
      font-weight: 550;
      display: inline-block;
      margin-bottom: 1rem;
    }
  }
}
</style>
