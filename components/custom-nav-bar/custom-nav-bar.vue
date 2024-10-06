<template>
  <view class="layout">
    <view class="navbar">
      <view class="statusBar" :style="{height:statusBarHeight+'px'}"></view>
      <view class="titleBar">
        <view class="title">
          {{title}}
        </view>
        <view class="search">
          <uni-icons class="icon" type="search" size="18" color="#888"></uni-icons>
          <text class="text">搜索</text>
        </view>
      </view>
    </view>
    <view class="fill">

    </view>
  </view>
</template>

<script setup>
  import {
    ref
  } from "vue";
  let SYSTEM_INFO = uni.getSystemInfoSync();
  let statusBarHeight = ref(SYSTEM_INFO.statusBarHeight);

  defineProps({
    title: {
      type: String,
      default: "未定义"
    }
  })
</script>

<style lang="scss" scoped>
  .layout {
    .navbar {
      background:
        linear-gradient(to bottom, transparent, #fff 400rpx),
        linear-gradient(to right, #beecd8 20%, #f4e2d8);
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 10;

      .titleBar {
        padding: 0 30rpx;
        display: flex;
        align-items: center;

        .title {
          font-size: 22px;
          font-weight: 700;
          color: #000;
        }

        .search {
          width: 220rpx;
          height: 50rpx;
          border-radius: 60rpx;
          background: rgba(255, 255, 255, 0.4);
          border: 1px solid #fff;
          margin-left: 30rpx;
          color: #999;
          font-size: 28rpx;
          display: flex;
          align-items: center;

          .icon {
            margin-left: 5rpx;
          }

          .text {
            padding-left: 10rpx;

          }
        }
      }
    }

    .fill {}
  }
</style>