<template>
  <view class="tab clearfix">
    <navigator open-type='switchTab' url='/pages/index/index' class="tab-box">首页
    </navigator>
    <navigator open-type='switchTab' url='/pages/fellow/fellow' class="tab-box">关注
    </navigator>
    <view class="tab-box">
      <view class="iconfont icon-tianjia icon-box"></view>
    </view>
    <navigator open-type='switchTab' url='/pages/message/message' class="tab-box">消息</navigator>
    <navigator open-type='switchTab' url='/pages/personal/personal' class="tab-box">我
    </navigator>
  </view>
</template>
<script>
export default {}
</script>
<style>
.tab {
  height: 50px;
  width: 100%;
  position: fixed;
  bottom: 0;
  left: 0;
  z-index: 22;
}
.tab-box {
  float: left;
  width: 20%;
  color: #fff;
  text-align: center;
  height: 50px;
  line-height: 50px;
}

.icon-box {
  width: 60%;
  height: 30px;
  background-color: #fff;
  color: black;
  margin: 10px 20%;
  line-height: 30px;
  border-radius: 5px;
  font-size: 15px;
}
</style>