<template>
  <view class="videoList">
    <view class="swiper-box">
      <swiper class="swiper" :vertical="true" @change="change" @touchstart="touchStart" @touchend="touchEnd">
        <swiper-item v-for="(item,index) of videos" :key="item.id">
          <view class="swiper-item">
            <video-player ref="video" :video='item' :index='index'></video-player>
          </view>
          <view class="left-box">
            <list-left :item="item"></list-left>
          </view>
          <view class="right-box">
            <list-right @open="openComment" :index='index' :item="item"></list-right>
          </view>
        </swiper-item>

      </swiper>
    </view>
    <view v-show='isShow' class="comment-box">
      <comment @close='closeComment'></comment>
    </view>
  </view>
</template>
<script>
import videoPlayer from './videoPlayer'
import listLeft from './listLeft'
import listRight from './listRight'
import comment from './comment'

export default {
  components: {
    videoPlayer,
    listLeft,
    listRight,
    comment,
  },
  props: ['list'],
  data() {
    return {
      videos: [],
      touchStartY: 0,
      touchEndY: 0,
      timer: null,
      page: 0,
      autoplay: false,
      isShow: false,
    }
  },
  watch: {
    list(newValue) {
      this.videos = newValue
      this.videos[0].autoplay = true
    },
  },
  onReady() {},
  methods: {
    change(e) {
      this.timer ? clearTimeout(this.timer) : null
      this.timer = setTimeout(() => {
        if (this.touchStartY > this.touchEndY && this.page < e.detail.current) {
          this.page = e.detail.current
          this.$refs.video[this.page].playAndSeek()
          this.$refs.video[this.page - 1].pause()
          this.touchStartY = 0
          this.touchEndY = 0
        } else if (
          this.touchStartY < this.touchEndY &&
          this.page > e.detail.current
        ) {
          this.page = e.detail.current
          this.$refs.video[this.page].playAndSeek()
          this.$refs.video[this.page + 1].pause()
          this.touchStartY = 0
          this.touchEndY = 0
        }
      }, 10)
    },
    touchStart(e) {
      this.touchStartY = e.changedTouches[0].pageY
    },
    touchEnd(e) {
      this.touchEndY = e.changedTouches[0].pageY
    },
    openComment() {
      this.isShow = true
    },
    closeComment() {
      this.isShow = false
    },
  },
}
</script>
<style>
.videoList {
  height: 100%;
  width: 100%;
  position: relative;
}

.swiper-box {
  height: 100%;
  width: 100%;
}
.swiper {
  height: 100%;
  width: 100%;
}
.swiper-item {
  height: 100%;
  width: 100%;
}

.left-box {
  position: absolute;
  bottom: 50px;
  left: 10px;
  z-index: 100;
}
.right-box {
  position: absolute;
  bottom: 50px;
  right: 10px;
  z-index: 100;
}

.comment-box {
  position: absolute;
  bottom: 0;
  left: 0;
  z-index: 23;

  height: 500px;
  width: 100%;
}
</style>