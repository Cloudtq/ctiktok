<template>
  <view class="followPlayer">
    <video id="myVideo" :autoplay="autoplay" class="video" objectFit='cover' loop='true' :src="'http://10.199.163.144:3000/video/'+item.src" :controls='false' @click='playerTo(list)'>
      <cover-view class="iconfont icon-bofang icon" @click='bofang'></cover-view>
    </video>
  </view>
</template>
<script>
export default {
  props: ['item', 'autoplay', 'list'],
  data() {
    return {
      videoContext: null,
      isPlay: true,
    }
  },
  onReady() {
    this.videoContext = uni.createVideoContext('myVideo', this)
  },

  methods: {
    play() {
      this.isPlay = true
      this.videoContext.play()
    },
    pause() {
      this.isPlay = false
      this.videoContext.pause()
    },
    bofang() {
      if (this.isPlay) this.pause()
      else this.play()
    },
    playerTo(list) {
      uni.setStorage({
        key: 'videoList',
        data: list,
      })
      uni.navigateTo({
        url: '/pages/player/player',
      })
    },
  },
}
</script>
<style>
.followPlayer {
  height: 100%;
  width: 100%;
}

.video {
  width: 80%;
  height: 100%;
  z-index: 19;
  position: relative;
}

.icon {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #fff;
  font-size: 20px;
}
</style>