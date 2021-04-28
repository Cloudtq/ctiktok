<template>
  <view class="">
    <view class="change-header">
      <navigator open-type='navigateBack' class="iconfont icon-back left">
      </navigator>
      <view class="title">
        切换城市
      </view>
    </view>
    <view class="around"></view>
  </view>

</template>
<script>
export default {}
</script>
<style>
.change-header {
  width: 100%;
  height: 80px;
  line-height: 80px;
  position: fixed;
  top: 0;
  left: 0;
  margin: 0 auto;
  background-color: #000;
}

.left {
  position: absolute;
  left: 15px;
  height: 80px;
  line-height: 80px;
  color: #aaa;
  font-size: 18px;
}

.title {
  font-size: 17px;
  text-align: center;
  color: white;
}

.around {
  width: 100%;
  height: 80px;
}
</style>