<template>
  <view class="members">
    <template v-for="member in members" :key="member.id">
      <view class="member">
        <view class="avatar">
          <image :src="member.avatar" class="img" />
        </view>
        <view class="info">
          <text class="name">{{ member.name }}</text>
          <text class="des">{{ member.des }}</text>
        </view>
      </view>
    </template>
  </view>
</template>

<script setup>
import { ref } from "vue";
import members from "../../mock/members";

</script>

<style lang="scss">
.members {
  overflow: auto;
  .member {
    display: flex;
    margin-bottom: 1rem;
    .avatar {
      width: 5rem;
      height: 5rem;
      .img {
        border-radius: 50%;
        width: 100%;
        height: 100%;
      }
    }
    .info {
      flex: 1;
      margin-left: 1rem;
      display: flex;
      flex-direction: column;
      .name {
        font-weight: 500;
        font-size: 1.2rem;
      }
      .nick-name,
      .des {
        font-size: 0.8rem;
        opacity: 0.5;
      }
    }
  }
}
</style>
