<template>
  <view class="right">
    <view class="author-img">
      <image class="img" src="../static/img/avatar.jpg" @click="click"></image>
      <view class="iconfont iconjiahao add" v-show="show" @click="hide">+</view>
    </view>
    <view class="iconfont icon-aixin right-box" :style="'color:'+color" @click="changeColor">
    </view>
    <view class="number">
      {{item.loveNumber}}
    </view>
    <view class="iconfont icon-pinglun right-box" @click="openComment">
    </view>
    <view class="number">
      {{item.commentNumber}}
    </view>
    <view class="iconfont icon-fenxiang right-box">
    </view>
    <view class="number">
      {{item.shareNumber}}
    </view>
    <view class="around">
      <image class="img" src="../static/img/around.jpg"></image>
    </view>
  </view>
</template>
<script>
export default {
  props: {
    item: {
      type: Object,
      default: () => ({}),
    },
    index: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      show: true,
      color: 'white',
      currindex: 0,
    }
  },
  onReady() {
    this.$bus.$on('changeColor', (index) => {
      if (index == this.currindex) this.changeColor()
    })
  },
  methods: {
    hide() {
      this.show = false
    },
    changeColor() {
      this.color === 'red' ? (this.color = 'white') : (this.color = 'red')
    },
    click() {
      uni.navigateTo({
        url: '/pages/user/user',
      })
    },
    openComment() {
      this.$emit('open')
    },
  },
  watch: {
    index: {
      handler(newValue) {
        this.currindex = newValue
      },
      immediate: true,
    },
  },
}
</script>
<style scoped>
.right {
  width: 50px;
  margin: 0 auto;
  color: white;
}
.author-img {
  position: relative;
  height: 50px;
  width: 50px;
  border-radius: 100px;
  border: 2px solid white;
}

.img {
  height: 50px;
  width: 50px;
  border-radius: 100px;
}

.right-box {
  width: 50px;
  height: 40px;
  margin-top: 13px;
  text-align: center;
  line-height: 40px;
  color: #fff;
  font-size: 33px;
}

.number {
  font-size: 10px;
  text-align: center;
  color: #fff;
}

.around {
  height: 50px;
  width: 50px;
  margin-top: 15px;
  animation: rotate 1.5s linear 0.2s infinite;
}

.add {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background-color: red;
  position: absolute;
  bottom: -9px;
  left: 16px;
  text-align: center;
  line-height: 18px;
  color: #fff;
  font-size: 12px;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>