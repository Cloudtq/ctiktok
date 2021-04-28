<template>
  <view class="personal">
    <view @click="back" class="iconfont icon-back iconback"></view>

    <person-info :pages='pages' @clickNow='clickNow' class=""></person-info>
    <person-list v-show="isShow[index]=='作品'" :currindex='index'></person-list>
    <follow-list :closeindex='closeIndex' v-show="isShow[index]=='动态'" :currindex='index' :topHeight='topHeight' :itemHeight='itemHeight' :autoplay="isShow[index]=='动态'?true:false" :video='list'>
    </follow-list>
    <person-list v-show="isShow[index]=='喜欢'" :currindex='index'></person-list>
  </view>
</template>
<script>
import personInfo from '../../components/personal/personInfo'
import personList from '../../components/personal/personalList'
import followList from '../../components/follow/followlist'

export default {
  components: {
    personInfo,
    personList,
    followList,
  },
  data() {
    return {
      list: [],
      isShow: ['作品', '动态', '喜欢'],
      index: 0,
      topHeight: 500,
      itemHeight: 550,
      closeIndex: 0,
      pages: 'user',
    }
  },
  methods: {
    getVideoInfo() {
      uni.request({
        url: 'http://localhost:3000/data',
        success: (res) => {
          this.list = res.data.list
        },
      })
    },
    clickNow(index) {
      this.closeIndex = this.index
      this.index = index
    },
    back() {
      uni.navigateBack({
        delta: 1,
      })
    },
  },
  created() {
    this.$on('clickNow', this.clickNow)
    this.getVideoInfo()
  },
}
</script>
<style >
.personal {
  width: 100%;
  height: 100%;
  background-color: #000;
  position: relative;
}

.iconback {
  z-index: 21;
  color: #fff;
  font-size: 17px;
  position: absolute;
  top: 30px;
  left: 10px;
}
</style>