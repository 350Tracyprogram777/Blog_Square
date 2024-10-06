<template>
  <view class="edit-page">
    <!-- 名称输入框 -->
    <view class="form-group">
      <input v-model="name" placeholder="请输入名称" class="input" :class="{ empty: !name }" />
    </view>

    <!-- 班级选择框 -->
    <view class="form-group">
      <select v-model="classGroup" class="select">
        <option value="">请选择班级</option>
        <option value="计科2201班">计科2201班</option>
        <option value="计科2202班">计科2202班</option>
        <option value="计科2203班">计科2203班</option>
        <option value="没班上">没班上</option>
      </select>
    </view>

    <!-- 确认修改按钮 -->
    <view class="form-group button-container">
      <button @click="handleConfirm" class="confirm-button">确认修改</button>
    </view>

    <!-- 提示框 -->
    <view v-if="message" class="alert">{{ message }}</view>
  </view>
</template>

<script setup>
  import {
    ref
  } from "vue";

  // 表单数据
  const name = ref("浙工商第一深情"); // 默认名称
  const classGroup = ref("计科2203班"); // 默认班级
  const message = ref(""); // 提示消息

  // 点击确认按钮的处理逻辑
  const handleConfirm = () => {
    if (!name.value || !classGroup.value) {
      message.value = "请填写完整！"; // 检查表单是否为空
    } else {
      message.value = "修改成功"; // 表单完整时显示修改成功
    }

    // 清除提示框，3秒后自动消失
    setTimeout(() => {
      message.value = "";
    }, 3000);
  };
</script>

<style scoped>
  .edit-page {
    display: flex;
    flex-direction: column;
    padding: 20px;
  }

  .form-group {
    margin-bottom: 20px;
  }

  .input,
  .select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
  }

  .input.empty::placeholder {
    color: #999;
  }

  .button-container {
    display: flex;
    justify-content: center;
  }

  .confirm-button {
    background-color: #4caf50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .confirm-button:hover {
    background-color: #45a049;
  }

  .alert {
    color: red;
    text-align: center;
    margin-top: 10px;
  }
</style>