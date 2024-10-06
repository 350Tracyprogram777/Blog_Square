<template>
  <view class="layout">
    <view class="row" v-for="item in arrs" :key="item.id" @click="goToDetail(item.id)">
      <view class="title">{{item.id}}.{{item.title}}</view>
      <view class="content">{{item.body}}</view>
    </view>
  </view>
</template>

<script setup>
  import {
    ref
  } from 'vue';
  let arrs = ref([])

  function request() {
    uni.showLoading()
    uni.request({
      url: "https://jsonplaceholder.typicode.com/posts",
      success: res => {
        console.log(res);
        arrs.value = res.data
      },
      fail: err => {
        console.log(err);
      },
      complete: () => {
        uni.hideLoading()
      }
    })
  }

  function goToDetail(id) {
    uni.navigateTo({
      url: "/pages/DetailComponent/DetailComponent?id=${id}" // 确保路径正确
    });
  }
  request();
</script>

<style lang="scss" scoped>
  .layout {
    padding: 30rpx;

    .row {
      border-bottom: 1px solid #cfcfcf;
      padding: 20rpx 0;

      .title {
        font-size: 48rpx;
        margin-bottom: 10rpx;
        color: skyblue;
      }

      .content {
        font-size: 28rpx;
        color: #666;
      }
    }

  }
</style>