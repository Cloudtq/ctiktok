<template>
  <view class="follow-list">
    <scroll-view style="height:100%;" scroll-y='true' @scroll="scroll">
      <view class="item" v-for="(item,index) of video" :key="index">
        <view class="top">
          <view class="img-box">
            <image class="img" src='../../static/img/avatar.jpg'></image>
          </view>
          <view class="autor-name">
            {{item.author}}
          </view>
          <view class="iconfont icon-more share">
          </view>
        </view>
        <view class="title">
          {{item.content}}
        </view>
        <view class="video-box">
          <follow-player :list='video' :autoplay='autoplay' ref="player" :item='item'></follow-player>
          <view class="music-box">
            <view class="music">{{item.musicName}}</view>
          </view>
        </view>
        <view class="box">
          <view class="left">
            4-25
          </view>
          <view class="right">
            <view class="iconfont icon-aixin icon">
              <text class="text">赞</text>
            </view>
            <view class="iconfont icon-pinglun icon">
              <text class="text">评论</text>
            </view>
            <view class="iconfont icon-fenxiang icon">
              <text class="text">分享</text>
            </view>
          </view>
        </view>
        <view class="comment">
          <view class="Number">
            4.2w评论过
          </view>
          <view class="comment-box">
            <view class="iconfont iconpen icon-pen"></view>
            <input class="input-box" type="text" placeholder="添加评论...">
          </view>
        </view>
      </view>
    </scroll-view>

  </view>
</template>
<script>
import followPlayer from './followPlayer'
export default {
  components: {
    followPlayer,
  },
  props: ['video', 'autoplay', 'topHeight', 'itemHeight', 'closeindex'],
  data() {
    return {
      index: 0,
    }
  },
  methods: {
    scroll(e) {
      // this.timer && clearTimeout(this.timer)
      // this.timer = setTimeout(() => {}, 100)
      const index = Math.floor(
        (e.detail.scrollTop + this.topHeight) / this.itemHeight
      )
      this.index = index
    },
  },
  watch: {
    index() {
      if (this.index >= 0 && this.index < this.video.length) {
        this.$refs.player[this.index].play()
      }
      if (this.index > 0) {
        this.$refs.player[this.index - 1].pause()
      }
      if (this.index < this.video.length - 1) {
        this.$refs.player[this.index + 1].pause()
      }
    },
    closeindex(newValue) {
      if (newValue == 1) {
        this.$refs.player[this.index].pause()
      }
    },
  },
}
</script>
<style >
.follow-list {
  margin-top: 10px;
  width: 100%;
  background-color: #000;
  padding-bottom: 50px;
  height: 100%;
}
.item {
  padding: 0 15px 20px;
}

.top {
  height: 40px;
}

.img-box {
  float: left;
}

.img {
  width: 35px;
  height: 35px;
  border-radius: 50%;
}

.autor-name {
  float: left;
  font-size: 14px;
  height: 35px;
  line-height: 35px;
  color: #fff;
  margin-left: 10px;
}

.share {
  float: right;
  font-size: 25px;
  margin-right: 10px;
  height: 35px;
  line-height: 35px;
  color: #fff;
}

.title {
  width: 100%;
  font-size: 13px;
  margin-top: 10px;
  height: 25px;
  line-height: 25px;
  color: #fff;
}

.video-box {
  width: 100%;
  height: 350px;
  position: relative;
}

.box {
  height: 25px;
  margin-top: 25px;
}

.left {
  float: left;
  font-size: 11px;
  height: 25px;
  line-height: 25px;
  color: #aaa;
}

.right {
  float: right;
  height: 25px;
}

.icon {
  font-size: 18px;
  float: right;
  color: #fff;
  margin-left: 10px;
}

.text {
  padding: 0 5px;
  font-size: 13px;
}

.comment {
  width: 100%;
}

.Number {
  width: 100%;
  height: 25px;
  font-size: 15px;
  line-height: 15px;
  color: #aaa;
  margin: 10px 0;
}

.comment-box {
  position: relative;
}

.icon-pen {
  height: 30px;
  color: #fff;
  position: absolute;
  top: 0;
  left: 0;
}

.input-box {
  margin-left: 28px;
  font-size: 15px;
}

.music-box {
  z-index: 20;
  position: absolute;
  bottom: 10px;
  left: 10px;
  width: 100px;
  overflow: hidden;
}

.music {
  color: #fff;
  font-size: 14px;
  width: 200px;
  animation: music 4s linear infinite;
}

scroll-view ::-webkit-scrollbar {
  width: 0;
  height: 0;
  background-color: transparent;
}
</style> 