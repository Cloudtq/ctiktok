<template>
  <view class="change-alphabet" @touchstart='touchStart' @touchend='touchEnd' @touchmove.stop.prevent="" @touchmove='touchMove'>
    <view class="list">
      <view class="item" v-for="item in citylist.city" :key="item.initial" hover-class='hover' @click="getInitial(item.initial)">
        {{item.initial}}
      </view>
    </view>

  </view>
</template>
<script>
export default {
  props: ['citylist'],
  data() {
    return {
      touch: false,
    }
  },
  methods: {
    getInitial(initial) {
      this.$bus.$emit('change', initial)
    },
    touchStart(e) {
      this.touch = true
    },
    touchEnd(e) {
      this.touch = false
    },
    touchMove(e) {
      let timer = null
      timer && clearTimeout(timer)
      timer = setTimeout(() => {
        if (this.touch) {
          //注意 clientY和pageY的区别
          let index = Math.floor((e.changedTouches[0].clientY - 150) / 15)
          if (index >= 0 && index < this.citylist.city.length) {
            this.$bus.$emit('change', this.citylist.city[index].initial)
          }
        }
      }, 30)
    },
  },
}
</script>
<style>
.change-alphabet {
  position: fixed;
  top: 150px;
  right: 0px;
}

.list {
  width: 30px;
}

.item {
  text-align: center;
  line-height: 15px;
  font-size: 12px;
  color: #fff;
}

.hover {
  text-align: center;
  line-height: 15px;
  font-size: 18px;
  color: aqua;
}
</style>