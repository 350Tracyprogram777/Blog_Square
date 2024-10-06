<template>
  <view class="userLayout pageBg">
    <view class="userInfo">
      <view class="avatar">
        <image src="../../static/logoZSH.jpg" mode="aspectFill"></image>
      </view>
      <view class="ip">浙工商第一深情</view>
      <view class="address">来自于：计科2203班</view>
    </view>
    <view class="section">
      <view class="list">
        <navigator url="/pages/classlist/classlist" class="nothing">
          <view class="row">
            <view class="left">
              <uni-icons type="star-filled" size="20" color="#28b389"></uni-icons>
              <view class="text">我的收藏</view>
            </view>
            <view class="right">
              <uni-icons type="right" size="15" color="#aaa"></uni-icons>
              <view class="text">33</view>
            </view>
          </view>
        </navigator>
        <navigator url="/pages/classlist/classlist" class="nothing">
          <view class="row">
            <view class="left">
              <uni-icons type="medal-filled" size="20" color="#28b389"></uni-icons>
              <view class="text">我的评分</view>
            </view>
            <view class="right">
              <uni-icons type="right" size="15" color="#aaa"></uni-icons>
              <view class="text">33</view>
            </view>
          </view>
        </navigator>
        <view class="row">
          <view class="left">
            <uni-icons type="person-filled" size="20" color="#28b389"></uni-icons>
            <view class="text">联系客服</view>
          </view>
          <!-- #ifdef H5 -->
          <button @click="clickContact">拨打电话</button>
          <!-- #endif -->
        </view>
      </view>
    </view>
    <view class="section">
      <view class="list">
        <navigator url="/pages/editPost/editPost">
          <view class="row">
            <view class="left">
              <uni-icons type="arrow-up" size="20" color="#28b389"></uni-icons>
              <view class="text">发布个人博客文章</view>
            </view>
          </view>
        </navigator>
        <navigator url="/pages/editPost/editPost">
          <view class="row">
            <view class="left">
              <uni-icons type="wallet-filled" size="20" color="#28b389"></uni-icons>
              <view class="text">管理个人博客文章</view>
            </view>
          </view>
        </navigator>
      </view>
    </view>
    <view class="section">
      <view class="list">
        <navigator url="/pages/editmyinfo/editmyinfo">
          <view class="row">
            <view class="left">
              <uni-icons type="pyq" size="20" color="#28b389"></uni-icons>
              <view class="text">管理账号</view>
            </view>
          </view>
        </navigator>
        <view class="row" @click="handleLogout">
          <view class="left">
            <uni-icons type="arrow-right" size="20" color="#28b389"></uni-icons>
            <view class="text">退出登录</view>
          </view>
        </view>
      </view>
    </view>
  </view>
  <div v-if="showMessage" class="message">{{ message }}</div>
</template>

<script setup>
  import {
    ref
  } from 'vue';

  // 定义响应式状态
  const showMessage = ref(false);
  const message = ref('');

  // 处理退出登录的函数
  const handleLogout = () => {
    // 设置提示信息
    message.value = '退出成功';
    showMessage.value = true;

    // 2秒后关闭提示框
    setTimeout(() => {
      showMessage.value = false;
    }, 2000);
  };
  const clickContact = () => {
    uni.makePhoneCall({
      phoneNumber: "19357396455"
    })
  }
</script>

<style lang="scss" scoped>
  .message {
    position: fixed;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    background-color: #28b389;
    color: white;
    padding: 10px 20px;
    border-radius: 5px;
    z-index: 1000;
    transition: opacity 0.5s;
  }

  .userLayout {
    .userInfo {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      padding: 50rpx 0;

      .avatar {
        width: 160rpx;
        height: 160rpx;
        border-radius: 50rpx;
        overflow: hidden;

        image {
          width: 100%;
          height: 100%;
        }
      }

      .ip {
        font-size: 44rpx;
        color: #333;
        padding: 20rpx 0 5rpx;
      }

      .address {
        font-size: 28rpx;
        color: #aaa;
      }
    }

    .section {
      width: 690rpx;
      margin: 50rpx auto;
      border-radius: 10rpx;
      border: 1px solid #eee;
      box-shadow: 0 0 30rpx rgba(0, 0, 0, 0.05);

      .list {
        .row {
          display: flex;
          justify-content: space-between;
          align-items: center;
          padding: 0 30rpx;
          height: 100rpx;
          position: relative;
          background-color: #fff;
          border-bottom: 1px solid #eee;

          &:last-child {
            border-bottom: 0
          }

          .left {
            display: flex;
            align-items: center;

            .text {
              padding-left: 20rpx;
              color: #666;
            }
          }

          .right {
            display: flex;
            align-items: center;

            .text {
              font-size: 28rpx;
              color: #aaa;

            }
          }

          button {
            position: absolute;
            top: 0;
            left: 0;
            height: 100rpx;
            width: 100%;
            opacity: 0;
          }
        }
      }
    }
  }
</style>