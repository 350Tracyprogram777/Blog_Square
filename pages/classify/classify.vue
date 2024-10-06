<template>
  <view class="classLayout pageBg">
    <custom-nav-bar title="分类页"></custom-nav-bar>
    <view class="classify">
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
      <theme-item imageSrc="../../common/images/cv.png" maskText="计算机视觉" tabText="11天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/phone.png" maskText="移动端开发" tabText="19天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/computerHistory.png" maskText="计算机历史" tabText="20天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/economic.png" maskText="经济学" tabText="6天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/psychology.png" maskText="心理学" tabText="2天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/me.png" maskText="机械工程" tabText="3天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/agriculture.png" maskText="农业学" tabText="1天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/political.png" maskText="政治学" tabText="17天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/art.png" maskText="艺术设计" tabText="7天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/history.png" maskText="历史学" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/philosophy.png" maskText="哲学" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/circuit.png" maskText="电子信息" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/ms.png" maskText="医学" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/basketball.png" maskText="体育" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/ed.png" maskText="教育" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/Boeing.png" maskText="航空航天" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/36.png" maskText="法学" tabText="24天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/5.png" maskText="天文学" tabText="12天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/35.png" maskText="玄学" tabText="187天前更新" :isMore="false"
        url="/pages/content/content" />
      <theme-item imageSrc="../../common/images/other.png" maskText="其他" tabText="16天前更新" :isMore="false"
        url="/pages/content/content" />

    </view>
  </view>
</template>

<script setup>

</script>

<style lang="scss" scoped>
  .classify {
    padding: 30rpx;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15rpx;
  }
</style>