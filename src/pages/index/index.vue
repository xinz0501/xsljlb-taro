<template>
  <scroll-view :scroll-y="true" :style="{ height: `calc(100vh - ${tabBarHeight}px)` }">
    <view class="index">
      <Home></Home>
    </view>
  </scroll-view>
  <AtTabBar
    id="tabBar"
    fixed
    :tabList="[{ title: '首页' }, { title: '我的' }]"
    @click="handleTabBarClick"
    :current="currentTabBar"
  />
</template>

<script setup>
import { onMounted, ref } from "vue";
import Home from "../home/index.vue";
import Taro from "@tarojs/taro";

let currentTabBar = ref(0);

const handleTabBarClick = (value) => {
  currentTabBar.value = value;
};

const tabBarHeight = ref(0);
const query = Taro.createSelectorQuery().select("#tabBar").boundingClientRect();
query.exec((res) => {
  if (res && res[0]) {
    tabBarHeight.value = res[0].height;
  }
});
</script>

<style lang="scss">
.index {
  padding: 0 1rem;
}
</style>
