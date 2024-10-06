<template>
  <view class="homeLayout pageBg">
    <custom-nav-bar title="主页"></custom-nav-bar>
    <view class="banner">
      <swiper circular indicator-dots indicator-color="rgba(255,255,255,0.5)" indicator-active-color="#fff" autoplay>
        <swiper-item>
          <image src="../../common/images/1.png" mdoe="aspectFill"></image>
        </swiper-item>
        <swiper-item>
          <image src="../../common/images/2.png" mdoe="aspectFill"></image>
        </swiper-item>
        <swiper-item>
          <image src="../../common/images/3.png" mdoe="aspectFill"></image>
        </swiper-item>
        <swiper-item>
          <image src="../../common/images/4.png" mdoe="aspectFill"></image>
        </swiper-item>
      </swiper>
    </view>
    <view class="notice">
      <view class="left">
        <uni-icons type="sound-filled" size="20" color="#28b389"></uni-icons>
        <test class="text">公告</test>
      </view>
      <view class="center">
        <swiper vertical autoplay interval="1500" duration="300" circular>
          <swiper-item v-for="item in 3">作者：计科2203——廖云星</swiper-item>
        </swiper>
      </view>
      <view class="right">
        <uni-icons type="arrow-right" size="16" color="#333"></uni-icons>
      </view>
    </view>
    <view class="select">
      <common-title>
        <template #name>当日热度排行</template>
        <template #custom>
          <view class="date">
            <uni-icons type="calendar" size="18" color="#28b389"></uni-icons>
            <view class="text">
              <uni-dateformat :date="Date.now()" format="yyyy.MM.dd"></uni-dateformat>
            </view>
          </view>
        </template>
      </common-title>
      <view class="layouts">
        <view class="rows" v-for="item in arrs" :key="item.id" @click="goToDetail(item.id)">
          <view class=" titles">{{item.id}}.{{item.title}}</view>
          <view class="contents">
            <image src="../../common/images/content.png" mode="aspectFill"></image>
            {{item.body}}
          </view>
        </view>
      </view>
    </view>
    <view class="theme">
      <common-title>
        <template #name>专题精选</template>
        <template #custom>
          <navigator url="/pages/classify/classify" open-type="reLaunch" class="more">More+</navigator>
        </template>
      </common-title>
      <view class="content">
        <theme-item imageSrc="../../common/images/back-development.png" maskText="后端开发" tabText="5天前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/SE.png" maskText="软件工程" tabText="3个月前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/ai.png" maskText="AI" tabText="5分钟前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/sql.png" maskText="数据库" tabText="5天前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/algorithm.png" maskText="算法" tabText="17分钟前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/os.png" maskText="操作系统" tabText="1天前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/fd.png" maskText="前端开发" tabText="3天前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item imageSrc="../../common/images/net.png" maskText="网络" tabText="17天前更新" :isMore="false"
          url="/pages/content/content" />
        <theme-item :isMore="true"></theme-item>
      </view>
    </view>
  </view>
</template>

<script setup>
  import {
    ref
  } from 'vue';
  let arrs = ref([])

  function request() {
    uni.request({
      url: "https://jsonplaceholder.typicode.com/posts",
      success: res => {
        console.log(res);
        arrs.value = res.data.slice(0, 5); // 截取id为1~5的几条
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
  .homeLayout {
    .banner {
      width: 750rpx;
      padding: 30rpx 0;

      swiper {
        width: 750rpx;
        height: 340rpx;

        &-item {
          width: 100%;
          height: 100%;
          padding: 0 30rpx;

          image {
            width: 100%;
            height: 100%;
            border-radius: 10rpx;
          }
        }
      }
    }

    .notice {
      width: 690rpx;
      height: 80rpx;
      line-height: 80rpx;
      background-color: #f9f9f9;
      margin: 0 atuo;
      border-radius: 80rpx;
      display: flex;

      .left {
        width: 140rpx;
        display: flex;
        align-items: center;
        justify-content: center;

        .text {
          color: "#28b389";
          font-weight: 600;
          font-size: 28;
        }
      }

      .center {
        flex: 1;

        swiper {
          height: 100%;

          &-item {
            height: 100%;
            font-size: 30rpx;
            color: #666;
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
          }
        }
      }

      .rigth {
        width: 70rpx;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }

    .select {
      padding-top: 50rpx;

      .layouts {
        padding: 30rpx;

        .rows {
          border-bottom: 1px solid #cfcfcf;
          padding: 20rpx 0;

          .titles {
            font-size: 35rpx;
            margin-bottom: 10rpx;
            color: skyblue;
          }

          .contents {
            font-size: 22rpx;
            color: #666;
            display: flex;
            align-items: center;

            image {
              height: 120rpx;
              margin-right: 10rpx;
            }
          }
        }

      }

      .date {
        color: #28b389;
        display: flex;
        align-items: center;

        .text {
          margin-left: 5rpx;
        }
      }

      .content {
        width: 720rpx;
        margin-left: 30rpx;
        margin-top: 30rpx;

        scroll-view {
          white-space: nowrap;

          .box {
            width: 200rpx;
            height: 430rpx;
            display: inline-block;
            margin-right: 15rpx;

            image {
              width: 100%;
              height: 100%;
              border-radius: 10rpx;
            }

            .mask {
              width: 100%;
              height: 70rpx;
              font-size: 30rpx;
              font-weight: 600;
              bottom: 0;
              left: 0;
              position: absolute;
              background: rgba(0, 0, 0, 0.2);
              color: #fff;
              display: flex;
              align-items: center;
              justify-content: center;
              backdrop-filter: blur(20rpx);
            }
          }

          .box:last-child {
            margin-right: 30rpx;
          }
        }
      }
    }

    .theme {
      padding: 50rpx 0;

      .more {
        font-size: 32rpx;
        color: #888;
      }

      .content {
        margin-top: 30rpx;
        padding: 30rpx;
        display: grid;
        gap: 15rpx;
        grid-template-columns: repeat(3, 1fr);
      }
    }
  }
</style>