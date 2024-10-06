<template>
  <view class="themeItem">
    <navigator :url="url" class="box" v-if="!isMore">
      <image class="pic" :src="imageSrc" mode="aspectFill"></image>
      <view class="mask">{{ maskText }}</view>
      <view class="tab">{{ tabText }}</view>
    </navigator>
    <navigator :url="moreUrl" open-type="reLaunch" class="box more" v-if="isMore">
      <image class="pic" :src="moreImageSrc" mode="aspectFill"></image>
      <view class="mask">
        <uni-icons type="more-filled" size="34" color="#fff"></uni-icons>
        <view class="text">{{ moreText }}</view>
      </view>
    </navigator>
  </view>
</template>

<script setup>
  const props = defineProps({
    imageSrc: {
      type: String,
      default: "../../common/images/6.png" // 默认图片
    },
    maskText: {
      type: String,
      default: "硬件" // 默认 mask 文本
    },
    tabText: {
      type: String,
      default: "三天前更新" // 默认 tab 文本
    },
    isMore: {
      type: Boolean,
      default: false // 是否显示更多
    },
    moreImageSrc: {
      type: String,
      default: "../../common/images/7.png" // 默认 "更多" 图片
    },
    moreText: {
      type: String,
      default: "更多" // "更多" 文本
    },
    url: {
      type: String,
      default: "/pages/content/content" // 默认导航链接
    },
    moreUrl: {
      type: String,
      default: "/pages/classify/classify" // 更多导航链接
    }
  });
</script>


<style lang="scss" scoped>
  .themeItem {
    .box {
      height: 340rpx;
      border-radius: 10rpx;
      overflow: hidden;
      position: relative;

      .pic {
        width: 100%;
        height: 100%;
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

      .tab {
        position: absolute;
        left: 0;
        top: 0;
        background: rgba(250, 129, 90, 0.7);
        backdrop-filter: blur(20rpx);
        color: #fff;
        font-size: 22rpx;
        padding: 6rpx 14rpx;
        border-radius: 0 0 20rpx 0;
      }
    }

    .box.more {
      .mask {
        width: 100%;
        height: 100%;
        flex-direction: column;
      }

      .text {
        font-size: 20rpx;
      }
    }
  }
</style>