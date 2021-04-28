<template>
  <view class="left">
    <view class="author">
      {{item.author}}
    </view>
    <view class="title">
      {{item.content}}
    </view>
    <view class="box">
      <view class="music">
        {{item.musicName}}
      </view>
    </view>
  </view>
</template>
<script>
export default {
  props: ['item'],
}
</script>
<style>
.left {
  height: 150px;
  margin-left: 10px;
  color: #fff;
  width: 150px;
}

.author {
  height: 35px;
  line-height: 35px;
  font-size: 15px;
}
.title {
  line-height: 22px;
  font-size: 12px;
  width: 100%;
  word-wrap: break-word;
}
.music {
  height: 35px;
  line-height: 35px;
  font-size: 12px;
  animation: music 4s linear 0.2s infinite;
}
.box {
  width: 100px;
  overflow: hidden;
}
</style>