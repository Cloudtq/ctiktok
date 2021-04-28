<template>
  <view class="box">
    <view class="followNav">
      <view class="iconfont icon-camera icon">
        <view class="icon-text">随拍</view>
      </view>
      <view class="middle">
        <navigator open-type='switchTab' :style="page=='follow'?active:''" class="text" url='/pages/fellow/fellow'>关注
        </navigator>
        <navigator open-type='switchTab' :style="page=='friends'?active:''" class="text" url='/pages/friends/friends'>好友</navigator>
      </view>
    </view>
    <view class="ground"></view>
  </view>

</template>
<script>
export default {
  props: ['page'],
  data() {
    return {
      active: 'border-bottom:2px solid #F0AD4E;',
    }
  },
}
</script>
<style>
.followNav {
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
  left: 5px;
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
  font-size: 15px;
  display: inline;
  color: #fff;
  margin: 10px;
}
.icon-text {
  margin-left: 10px;
  font-size: 15px;
}

.ground {
  width: 100%;
  height: 60px;
}
</style>