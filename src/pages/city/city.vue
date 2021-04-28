<template>
  <view class="city">
    <first-nav></first-nav>
    <tab-bar></tab-bar>
    <city-content :cityName='cityName'></city-content>
  </view>
</template>
<script>
import tabBar from '../../components/tab'
import firstNav from '../../components/first-nav'
import cityContent from '../../components/cityContent'
export default {
  components: {
    tabBar,
    firstNav,
    cityContent,
  },
  data() {
    return {
      cityName: '',
    }
  },
  onShow() {
    uni.getStorage({
      key: 'city',
      success: (res) => {
        this.cityName = res.data
      },
    })
  },
}
</script>
<style>
.city {
  width: 100%;
  height: 100%;
  background-color: #000;
}
</style>