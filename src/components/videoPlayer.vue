<template>
  <view class="videoPlayer">
    <video id="myVideo" class="video" :autoplay='autoplay' :controls="false" :loop="true" :src="'http://localhost:3000/video/'+video.src" @click="click"></video>
  </view>
</template>
<script>
export default {
  props: ['video', 'index'],
  data() {
    return {
      videoContext: null,
      play: true,
      dbClick: false,
      timer: null,
      autoplay: false,
    }
  },
  onReady() {
    this.index == 0 ? (this.autoplay = true) : (this.autoplay = false)
    this.videoContext = uni.createVideoContext('myVideo', this)
  },
  methods: {
    playAndSeek() {
      this.videoContext.seek(0)
      this.videoContext.play()
    },
    pause() {
      this.videoContext.pause()
    },
    playThis() {
      this.videoContext.play()
    },

    click() {
      this.timer && clearTimeout(this.timer)
      this.dbClick = !this.dbClick
      this.timer = setTimeout(() => {
        if (this.dbClick) {
          this.start()
        } else {
          this.$bus.$emit('changeColor', this.index)
        }
        this.dbClick = false
      }, 300)
    },
    start() {
      if (this.play === false) {
        this.playThis()
        this.play = true
      } else {
        this.pause()
        this.play = false
      }
    },
  },
}
</script>
<style>
.videoPlayer {
  width: 100%;
  height: 100%;
}

.video {
  width: 100%;
  height: 100%;
}
</style>