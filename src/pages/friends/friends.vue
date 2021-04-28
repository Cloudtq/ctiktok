<template>
  <view class="friends">
    <view class="space"></view>
    <fellow-header :page='page'></fellow-header>
    <follow-list :autoplay='true' :topHeight='topHeight' :itemHeight='itemHeight' :video='video'></follow-list>
    <tab-bar></tab-bar>
  </view>
</template>
<script>
import fellowHeader from '../../components/follow/fellowHeader'
import tabBar from '../../components/tab'
import followList from '../../components/follow/followlist'

export default {
  components: {
    fellowHeader,
    tabBar,
    followList,
  },
  data() {
    return {
      page: 'friends',
      video: [],
      topHeight: 150,
      itemHeight: 550,
    }
  },
  created() {
    this.getVideo()
  },
  methods: {
    getVideo() {
      uni.request({
        url: 'http://localhost:3000/data',
        success: (res) => {
          this.video = res.data.list
        },
      })
    },
  },
}
</script>
<style >
.friends {
  width: 100%;
  height: 100%;
  background-color: #000;
}
</style>