<template>
  <view class="firNav">
    <view class="iconfont icon-search icon"></view>
    <view class="middle">
      <navigator open-type='switchTab' class="text" url='/pages/index/index'>推荐
      </navigator>
      <navigator open-type='navigate' class="text" url='/pages/city/city'>同城</navigator>
    </view>
  </view>
</template>
<script>
export default {}
</script>
<style>
.firNav {
  width: 100%;
  position: fixed;
  top: 25px;
  left: 0;
  height: 35px;
  line-height: 35px;
  margin: 0 auto;
  z-index: 10;
}

.icon {
  position: absolute;
  left: 0;
  top: 0;
  text-align: center;
  width: 20%;
  font-size: 20px;
  color: #fff;
}

.middle {
  text-align: center;
}

.text {
  display: inline;
  color: #fff;
  margin: 0 10px;
}
</style>