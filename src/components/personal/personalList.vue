<template>

  <view class="">
    <view class="person-list">
      <view class="item">
        <video class="video" objectFit='cover' src="http://localhost:3000/video/1" :controls='false'></video>
        <view class="love-box">
          <text class="iconfont icon-aixin love-icon">12w</text>
        </view>
      </view>
      <view class="item">
        <video class="video" objectFit='cover' src="http://localhost:3000/video/1" :controls='false'></video>
        <view class="love-box">
          <text class="iconfont icon-aixin love-icon">12w</text>
        </view>
      </view>
      <view class="item">
        <video class="video" objectFit='cover' src="http://localhost:3000/video/1" :controls='false'></video>
        <view class="love-box">
          <text class="iconfont icon-aixin love-icon">12w</text>
        </view>
      </view>
      <view class="item">
        <video class="video" objectFit='cover' src="http://localhost:3000/video/1" :controls='false'></video>
        <view class="love-box">
          <text class="iconfont icon-aixin love-icon">12w</text>
        </view>
      </view>
    </view>
    <view class="more">
      没有更多了
    </view>
    <view class="ground">

    </view>
  </view>

</template>
<script>
export default {}
</script>
<style >
.person-list {
  width: 100%;
  overflow: hidden;
  background-color: #000;
  padding: 0 0.5%;
}

.item {
  width: 33%;
  height: 150px;
  float: left;
  position: relative;
}

.love-box {
  position: absolute;
  bottom: 5px;
  left: 10px;
}

.love-icon {
  font-size: 14px;
  color: #fff;
}

.video {
  width: 100%;
  height: 100%;
}

.ground {
  width: 100%;
  height: 50px;
  background-color: #000;
}

.more {
  padding-top: 10px;
  background-color: #000;
  width: 100%;
  height: 30px;
  line-height: 30px;
  text-align: center;
  font-size: 12px;
  color: #999;
}
</style>