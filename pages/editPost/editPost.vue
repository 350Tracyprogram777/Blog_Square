<template>
  <view class="publish-page">
    <!-- 标题输入框 -->
    <view class="form-group">
      <input v-model="title" placeholder="请输入标题" class="input" :class="{ empty: !title }" />
    </view>

    <!-- 分类选择框 -->
    <view class="form-group">
      <select v-model="category" class="select">
        <option value="其他">其他</option>
        <option value="软件工程">软件工程</option>
        <option value="AI">AI</option>
        <option value="数据库">数据库</option>
        <option value="算法">算法</option>
        <option value="操作系统">操作系统</option>
        <option value="前端开发">前端开发</option>
        <option value="计算机视觉">计算机视觉</option>
        <option value="移动端开发">移动端开发</option>
        <option value="计算机历史">计算机历史</option>
        <option value="经济学">经济学</option>
        <option value="心理学">心理学</option>
        <option value="电子信息">电子信息</option>
        <option value="医学">医学</option>
        <option value="体育">体育</option>
        <option value="教育">教育</option>
        <option value="航空航天">航空航天</option>
        <option value="哲学">哲学</option>
        <option value="历史学">历史学</option>
        <option value="艺术设计">艺术设计</option>
        <option value="机械工程">机械工程</option>
        <option value="农业学">农业学</option>
        <option value="政治学">政治学</option>
      </select>
    </view>

    <!-- 内容输入框 -->
    <view class="form-group">
      <textarea v-model="content" placeholder="请输入内容" class="textarea"></textarea>
    </view>

    <!-- 发布按钮 -->
    <view class="form-group button-container">
      <button @click="handlePublish" class="publish-button">发布</button>
    </view>

    <!-- 提示框 -->
    <view v-if="message" class="alert">{{ message }}</view>
  </view>
</template>

<script setup>
  import {
    ref
  } from "vue";

  // 双向绑定的表单数据
  const title = ref(""); // 标题
  const category = ref("其他"); // 分类默认值
  const content = ref(""); // 内容
  const message = ref(""); // 提示消息

  // 点击发布按钮的处理逻辑
  const handlePublish = () => {
    if (!title.value || !category.value || !content.value) {
      message.value = "请填写完整！"; // 当表单不完整时显示提示
    } else {
      message.value = "发布成功"; // 当表单完整时显示发布成功
    }

    // 清除提示框，3秒后消失
    setTimeout(() => {
      message.value = "";
    }, 3000);
  };
</script>

<style scoped>
  .publish-page {
    display: flex;
    flex-direction: column;
    padding: 20px;
  }

  .form-group {
    margin-bottom: 20px;
  }

  .input,
  .textarea,
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

  .textarea {
    height: 200px;
  }

  .button-container {
    display: flex;
    justify-content: center;
  }

  .publish-button {
    background-color: #4caf50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .publish-button:hover {
    background-color: #45a049;
  }

  .alert {
    color: red;
    text-align: center;
    margin-top: 10px;
  }
</style>