<script>
export default {
  onLaunch: function () {
    console.log('App Launch')
    uni.hideTabBar()
  },
  onShow: function () {
    console.log('App Show')
  },
  onHide: function () {
    console.log('App Hide')
  },
}
</script>

<style>
@import './style/iconfont.css';

/*每个页面公共css */
html,
body {
  height: 100%;
  width: 100%;
}
</style>
