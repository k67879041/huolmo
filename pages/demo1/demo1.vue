<template>
  <view class="container">
    <view class="logo-container">
      <view class="logo-bg">
        <image 
          class="logo" 
          src="/static/logo.png" 
          mode="aspectFit"
          alt="Logo"
        />
      </view>
      <view class="text">{{ subtitle }}</view>
    </view>
    <text class="title">{{ title }}</text>
  </view>
</template>

<script setup>
import { ref } from 'vue'



// 可配置的文案，便于后期修改
const title = ref('demo1测试')
const subtitle = ref('我的')   // 原占位符，现改为变量
</script>

<style lang="scss" scoped>
// 定义设计令牌（Design Tokens）
$primary-text-color: #8f8f94;
$font-size-md: 36rpx;
$avatar-size: 200rpx;
$spacing-sm: 20rpx;

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  
  .logo-container {
    display: flex;
	flex-direction: column;
    align-items: center;       // 垂直居中圆形和文字
    justify-content: center;

    .logo-bg {
      height: $avatar-size;
      width: $avatar-size;
      border-radius: 50%;
      overflow: hidden;
      flex-shrink: 0;          // 防止压缩变形
    }

    .logo {
      height: 100%;
      width: 100%;
    }

    .text {
      margin-left: $spacing-sm;
      font-size: $font-size-md;
      color: $primary-text-color;
      // 删除冗余的 flex 布局，文本自然居中
      line-height: 1.4;         // 提升可读性
    }
  }

  .title {
    margin-top: $spacing-sm;    // 与上方的 logo-container 拉开间距
    font-size: $font-size-md;
    color: $primary-text-color;
  }
}
</style>