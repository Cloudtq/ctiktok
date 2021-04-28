<template>
  <view class="cityList">
    <scroll-view class="scrolly" scroll-y='true' :scroll-into-view="viewId">
      <view class="city-box">
        <view class="box">
          <view class="title">
            <icon class="iconfont icon-iconset0391"></icon>自动定位
          </view>
          <view class="currentCity">{{cityName}}</view>
        </view>
        <view class="box">
          <view class="title">
            热门城市
          </view>
          <view class="hotlist">
            <view class="item" v-for="(item,index) of list" :key="index">
              {{item}}
            </view>
          </view>
        </view>
        <view class="box-list" v-for="(item,index) of citylist.city" :key="index">
          <view class="initial" :id="item.initial">
            {{item.initial}}
          </view>
          <view class="city-name" v-for="listitem of item.list" :key="listitem.label" @click="chooseCity(listitem.name)">
            {{listitem.name}}
          </view>
        </view>
      </view>
    </scroll-view>
  </view>
</template>
<script>
export default {
  props: ['citylist'],
  data() {
    return {
      list: [
        '深圳',
        '上海',
        '北京',
        '广州',
        '重庆',
        '西安',
        '成都',
        '武汉',
        '苏州',
        '南京',
        '郑州',
        '厦门',
        '杭州',
      ],
      viewId: '',
      cityName: '北京',
    }
  },
  beforeCreate() {
    this.$bus.$on('change', (initial) => {
      this.viewId = initial
    })
  },
  methods: {
    chooseCity(cityName) {
      uni.setStorage({
        key: 'city',
        data: cityName,
        success: function () {
          console.log('success')
        },
      })

      uni.getStorage({
        key: 'city',
        success: (res) => {
          this.cityName = res.data
        },
      })

      uni.redirectTo({
        url: '/pages/city/city',
      })
    },
  },
}
</script>
<style scoped>
.cityList {
  width: 100%;
  background-color: #000;
  height: 100%;
}

.box {
  background-color: #222;
  margin-top: 10px;
  padding: 0px 20px 20px 5px;
}

.title {
  height: 40px;
  line-height: 40px;
  margin-left: 15px;
  color: #fff;
  font-size: 14px;
}

.currentCity {
  color: #aaa;
  font-size: 14px;
  margin-left: 15px;
  height: 30px;
  line-height: 30px;
}

.hotlist {
  width: 100%;
  overflow: hidden;
}

.item {
  width: 30%;
  height: 28px;
  line-height: 28px;
  font-size: 12px;
  background-color: #333;
  margin-left: 2.5%;
  margin-bottom: 10px;
  text-align: center;
  color: #aaa;
  float: left;
}

.box-list {
  padding: 8px, 5px;
}

.initial {
  height: 25px;
  line-height: 25px;
  background-color: #000;
  padding-left: 10px;
  color: #666;
  font-size: 12px;
}

.city-name {
  background-color: #222;
  height: 40px;
  line-height: 40px;
  padding-left: 10px;
  color: #aaa;
  font-size: 15px;
}

.scrolly {
  height: 100%;
}
</style>