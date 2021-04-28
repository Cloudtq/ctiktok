<template>
  <view class="content">
    <first-nav></first-nav>
    <video-list :list='list'></video-list>
    <tab-bar></tab-bar>
  </view>
</template>

<script>
import tabBar from '../../components/tab'
import firstNav from '../../components/first-nav'
import videoList from '../../components/videoList'
export default {
  data() {
    return {
      title: 'Hello',
      list: [],
    }
  },
  components: {
    tabBar,
    firstNav,
    videoList,
  },
  beforeCreate() {
    uni.request({
      url: 'http://localhost:3000/data',
      success: (res) => {
        this.list = res.data.list
      },
    })
  },
  FirstNavonLoad() {},
  methods: {},
}
</script>

<style>
.content {
  width: 100%;
  height: 100%;
}
</style>
