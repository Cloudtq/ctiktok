<template>
  <view class="city-content">
    <view class="location">
      <view class="iconfont icon-iconset0391 loc-left">
        自动定位：{{cityName}}
      </view>
      <navigator url='/pages/changeCity/changeCity' class="loc-right">
        切换<text class="iconfont icon-right" style="font-size:12px"></text>
      </navigator>
    </view>
    <view class="video-list">
      <view class="item">
        <view class="video">
          <video objectFit='fill' style="width:100%;height:100%;" src="http://localhost:3000/video/1" controls='false'></video>
        </view>
        <view class="img">
          <image class="img-avator" src="../static/img/avatar.jpg"></image>
        </view>
      </view>
      <view class="item">
        <view class="video">
          <video objectFit='fill' style="width:100%;height:100%;" src="http://localhost:3000/video/1" controls='false'></video>
        </view>
        <view class="img">
          <image class="img-avator" src="../static/img/avatar.jpg"></image>
        </view>
      </view>
      <view class="item">
        <view class="video">
          <video objectFit='fill' style="width:100%;height:100%;" src="http://localhost:3000/video/1" controls='false'></video>
        </view>
        <view class="img">
          <image class="img-avator" src="../static/img/avatar.jpg"></image>
        </view>
      </view>
      <view class="item">
        <view class="video">
          <video objectFit='fill' style="width:100%;height:100%;" src="http://localhost:3000/video/1" controls='false'></video>
        </view>
        <view class="img">
          <image class="img-avator" src="../static/img/avatar.jpg"></image>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  props: ['cityName'],
  data() {
    return {}
  },
}
</script>
<style>
.cityContent {
  width: 100%;
  background-color: #000;
  z-index: 10;
}
.location {
  width: 100%;
  height: 40px;
  padding-top: 70px;
  overflow: hidden;
  color: #aaa;
}
.loc-left {
  float: left;
  padding-left: 15px;
  font-size: 12px;
}
.loc-right {
  float: right;
  padding-right: 15px;
  font-size: 12px;
}

.video-list {
  width: 100%;
  overflow: auto;
  background-color: #000;
}

.item {
  width: 50%;
  float: left;
  position: relative;
}

.video {
  width: 92%;
  height: 300px;
  margin-left: 4%;
}

.img {
  position: absolute;
  bottom: 7px;
  right: 15px;
}

.img-avator {
  border-radius: 50%;
  width: 30px;
  height: 30px;
}
</style>