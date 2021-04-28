<template>
  <view class="person-info">
    <view class="background-img-box">
      <image class="background-img" src="../../static/img/bc.png"></image>
    </view>
    <view class="top">
      <view class="personal-img-box">
        <image class="personal-img" src='../../static/img/avatar.jpg'></image>
      </view>
      <view class="change" :style='isActive?"":style' @click="changeInfo">{{pages=='user'?text:'编辑资料'}}</view>
    </view>
    <view class="name-box">
      <view class="name">czd</view>
      <view class="douyinId">抖音号:115sa151</view>
    </view>
    <view class="text-box">
      <view class="introduce">
        我爱学习
      </view>
      <view class="label-box">
        <view class="label">111</view>
        <view class="label">222</view>
      </view>
      <view class="number-box">
        <view class="box">
          <text class="num">123</text>
          <text class="num-text">获赞</text>
        </view>
        <view class="box">
          <text class="num">123</text>
          <text class="num-text">关注</text>
        </view>
        <view class="box">
          <text class="num">123</text>
          <text class="num-text">粉丝</text>
        </view>
      </view>
    </view>
    <view class="add-box">
      <text class="iconfont icon-suipaihudong"></text>
      <text class="add">添加随拍</text>
    </view>

    <view class="option-box">
      <view class="option" v-for="(item,index) of options" :key="index" @click="currIndex(index)">
        <span class="option-text" :class="index==currentIndex?'active':''">{{item}}</span>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  props: ['pages'],
  data() {
    return {
      options: ['作品', '动态', '喜欢'],
      currentIndex: 0,
      style: 'background:red',
      isActive: false,
      text: ' + 关注',
    }
  },
  created() {
    this.$emit('clickNow', this.currentIndex)
  },
  methods: {
    currIndex(index) {
      this.$emit('clickNow', index)
      this.currentIndex = index
    },
    changeInfo() {
      if (this.pages == 'personal') {
        uni.navigateTo({
          url: '/pages/changeInfo/changeInfo',
        })
      } else if (this.pages == 'user') {
        this.isActive = !this.isActive
        if (this.isActive) {
          this.text = '取消关注'
        } else {
          this.text = ' + 关注'
        }
      }
    },
  },
  onLoad() {},
}
</script>
<style >
.person-info {
  width: 100%;
  background-color: #000;
}

.background-img-box {
  width: 100%;
  padding: 0 1px;
  z-index: 19;
}

.background-img {
  width: 100%;
  height: 180px;
}

.top {
  width: 100%;
  position: absolute;
  top: 140px;
  left: 0;
  z-index: 20;
  height: 70px;
  background-color: #000;
}

.personal-img-box {
  margin: -20px 0 0 30px;
}

.personal-img {
  border: 3.5px solid #000;
  width: 80px;
  height: 80px;
  border-radius: 50%;
}

.change {
  position: absolute;
  top: 15px;
  right: 75px;
  width: 43%;
  height: 35px;
  line-height: 35px;
  font-size: 16px;
  text-align: center;
  background-color: #333;
  border-radius: 2px;
  color: #fff;
}

.name-box {
  margin-top: 25px;
  padding: 0 25px;
  color: #eee;
}
.name {
  height: 50px;
  line-height: 50px;
  font-size: 26px;
}

.douyinId {
  height: 25px;
  line-height: 25px;
  font-size: 14px;
}

.text-box {
  padding: 0 25px;
  margin-top: 8px;
  border-top: 1px solid #222;
}

.introduce {
  height: 30px;
  line-height: 30px;
  font-size: 15px;
  color: #eee;
}

.label-box {
  margin-top: 5px;
  width: 100%;
  height: 25px;
  line-height: 25px;
  color: #eee;
}

.label {
  height: 20px;
  padding: 0 5px;
  line-height: 20px;
  font-size: 11.5px;
  background-color: #333;
  color: #999;
  float: left;
  border-radius: 1.5px;
  margin-right: 10px;
}

.number-box {
  width: 100%;
  height: 50px;
  line-height: 50px;
}

.box {
  height: 40px;
  line-height: 40px;
  float: left;
  margin-right: 5px;
}

.num {
  color: #fff;
  font-size: 15px;
}

.num-text {
  color: #999;
  font-size: 13px;
}

.add-box {
  margin: 0 6%;
  height: 40px;
  line-height: 40px;
  background-color: #333;
  border-radius: 3px;
  text-align: center;
  color: #fff;
}

.add {
  padding-left: 5px;
  font-size: 13px;
}

.option-box {
  margin-bottom: 10px;
  width: 100%;
  height: 50px;
  line-height: 50px;
}

.option {
  width: 33%;
  height: 50px;
  line-height: 50px;
  color: #999;
  float: left;
  text-align: center;
}

.active {
  border-bottom: 2px solid aqua;
}

.option-text {
  padding-bottom: 5px;
}
</style>