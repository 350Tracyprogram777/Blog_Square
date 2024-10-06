<template>
  <view class="layout">
    <view class="row" v-for="item in arrs" :key="item.id">
      <view class="title">{{item.title}}</view>
      <image src="../../common/images/content.png" mode="aspectFill"></image>
      <view class="content">{{item.body}}</view>
    </view>
    <view class="footer">
      <view class="box">
        <uni-icons type="star" size="23"></uni-icons>
        <view class="text">收藏</view>
      </view>
      <view class="box" @click="clickScore">
        <uni-icons type="vip" size="23"></uni-icons>
        <view class="text">评分</view>
      </view>
      <view class="box" @click="clickInfo">
        <uni-icons type="compose" size="23"></uni-icons>
        <view class="text">评论</view>
      </view>
      <view class="box">
        <uni-icons type="undo" size="23"></uni-icons>
        <view class="text">分享</view>
      </view>
      <view class="box">
        <uni-icons type="more-filled" size="23"></uni-icons>
        <view class="text">更多</view>
      </view>
    </view>
  </view>
  <uni-popup ref="infoPopup" type="bottom">
    <view class="infoPopup">
      <view class="popHeader">
        <view></view>
        <view class="title">评论信息</view>
        <view class="close" @click="clickInfoClose">
          <uni-icons type="closeempty" size="18" color="#999"></uni-icons>
        </view>
      </view>
      <scroll-view scroll-y>
        <view class="content">
          <view class="row" v-for="item in 20">
            <view class="avatar">
              <image src="../../static/logoZSH.jpg" mode="aspectFill"></image>
            </view>
            <view class="custom">匿名：</view>
            <view class="conment">老师，我太想进步了！</view>
          </view>
        </view>
      </scroll-view>
    </view>
  </uni-popup>
  <uni-popup ref="scorePopup" :is-mask-click="false">
    <view class="scorePopup">
      <view class="popHeader">
        <view></view>
        <view class="title">文章评分</view>
        <view class="close" @click="clickScoreClose">
          <uni-icons type="closeempty" size="18" color="#999"></uni-icons>
        </view>
      </view>
      <view class="content">
        <uni-rate v-model="useScore" allow-half />
      </view>
      <view class="footer">
        <button @click="submitScore" :disabled="!useScore" type="default" size="mini" plain>确认评分</button>
      </view>
    </view>
  </uni-popup>
</template>

<script setup>
  import {
    ref
  } from 'vue';
  let arrs = ref([]);
  const infoPopup = ref(null);
  const scorePopup = ref(null);
  const useScore = ref(0);
  //评论弹窗
  const clickInfo = () => {
    infoPopup.value.open();
  }
  const clickInfoClose = () => {
    infoPopup.value.close();
  }
  //评分！！！
  const submitScore = () => {
    console.log("提交评分")
  }
  const clickScore = () => {
    scorePopup.value.open();
  }
  const clickScoreClose = () => {
    scorePopup.value.close();
  }

  function request() {
    uni.showLoading()
    uni.request({
      url: "https://jsonplaceholder.typicode.com/posts?id=1",
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

  request();
</script>

<style lang="scss" scoped>
  .popHeader {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .title {
      color: #676767;
      font-size: 26rpx;
    }

    .close {
      padding: 6rpx;
    }
  }

  .infoPopup {
    background: #cfcfcf;
    padding: 30rpx;
    border-radius: 30rpx 30rpx 0 0;
    overflow: hidden;

    scroll-view {
      max-height: 60vh;

      .content {
        .row {
          display: flex;
          padding: 16rpx 0;
          line-height: 1.7em;

          .custom {
            color: #000;
            font-size: 25rpx;
          }

          .conment {
            font-size: 40rpx;
          }

          .avatar {
            width: 120rpx;
            height: 120rpx;
            border-radius: 10rpx;
            overflow: hidden;

            image {
              width: 100%;
              height: 100%;
            }
          }
        }
      }
    }
  }

  .scorePopup {
    background: #fff;
    padding: 30rpx;
    width: 70vw;
    border-radius: 30rpx;

    .content {
      padding: 30rpx 0;
      display: flex;
      justify-content: center;
      align-items: center;

    }

    .footer {

      padding: 10rpx 0;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }

  .layout {
    padding: 30rpx;
    position: relative;
    width: 100%;
    height: 100vh;

    .row {
      border-bottom: 1px solid #cfcfcf;
      padding: 20rpx 0;

      .title {
        font-size: 50rpx;
        margin-bottom: 10rpx;
        color: skyblue;
      }

      .content {
        font-size: 35rpx;
        color: #666;
      }
    }

    .footer {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background-color: #f8f8f8;
      /* Footer 背景色 */
      display: flex;
      justify-content: space-around;
      padding: 10px 0;
      box-shadow: 0 -1px 5px rgba(0, 0, 0, 0.1);
      /* 添加阴影效果 */
      z-index: 999;
      /* 保证 footer 不会被其他内容覆盖 */


      .box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
      }
    }

  }
</style>