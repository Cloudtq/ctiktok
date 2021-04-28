<template>
  <view class="change-city">
    <change-header></change-header>
    <city-list :citylist='city'></city-list>
    <change-alphabet :citylist='city'></change-alphabet>
  </view>
</template>
<script>
import changeHeader from '../../components/changeCity/changeHeader'
import cityList from '../../components/changeCity/cityList'
import changeAlphabet from '../../components/changeCity/changeAlphabet'

export default {
  components: {
    changeHeader,
    cityList,
    changeAlphabet,
  },
  data() {
    return {
      city: [],
    }
  },
  created() {
    //请求城市数据
    uni.request({
      url: 'http://localhost:3000/city',
      success: (res) => {
        this.city = res.data
      },
    })
  },
}
</script>
<style>
.change-city {
  width: 100%;
  background-color: #000;
  height: 100%;
}
</style>