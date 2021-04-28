<template>
  <view class="modify">
    <view class="nav-box">
      <navigator open-type='redirect' url='/pages/changeInfo/changeInfo' class="iconfont icon-back icon-box"></navigator>
      <view class="title">修改{{title}}</view>
    </view>
    <view class="box">
      <view class="text">
        我的{{title}}
      </view>
      <view v-if="title==='昵称'" class="input-name">
        <input class="input" type="text" v-model="value" maxlength="20" placeholder="请输入昵称" />
        <icon class="iconfont icon-delete delete" @click='clearInput'></icon>
        <view class="number">{{value.length}}/20</view>
        <view class="footer" @click='saveName'>
          保存
        </view>
      </view>
      <view v-if="title==='抖音号'" class="input-name">
        <input class="input" type="text" v-model="value" maxlength="16" placeholder="请输入抖音号" />
        <icon class="iconfont icon-delete delete" @click='clearInput'></icon>
        <view class="number">最多16个字，只允许包含字母、数字、下划线和点。30天内仅能修改一次。</view>
        <view class="footer" @click='saveId'>
          保存
        </view>
      </view>
      <view v-if="title==='简介'" class="input-name">
        <textarea v-model="content" placeholder="填写个人简介更容易获得别人的关注哦" class="text-area" name="" id="" cols="30" rows="10"></textarea>
        <view class="footer" @click='saveContent'>
          保存
        </view>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {
      value: 'czd',
      title: '',
      content: '',
    }
  },
  onLoad(res) {
    this.value = res.value
    this.title = res.title
  },
  methods: {
    clearInput() {
      this.newName = ''
    },
    saveName() {
      uni.setStorage({
        key: 'username',
        data: this.value,
      })
    },
    saveId() {
      uni.setStorage({
        key: 'userId',
        data: this.value,
      })
    },
    saveContent() {
      uni.setStorage({
        key: 'content',
        data: this.content,
      })
    },
  },
}
</script>
<style >
.modify {
  width: 100%;
  height: 100%;
  background-color: #000;
}

.nav-box {
  height: 50px;
  position: relative;
  padding-top: 30px;
  margin: 0 auto;
}

.icon-box {
  position: absolute;
  top: 30px;
  left: 10px;
  font-size: 15px;
  color: #fff;
}

.title {
  text-align: center;
  font-size: 16px;
  color: #fff;
}

.box {
  padding: 15px;
}

.text {
  color: #999;
  font-size: 13px;
}

.input-name {
  margin-top: 10px;
  font-size: 15px;
  position: relative;
}

.input {
  width: 95%;
  color: #fff;
}

.delete {
  position: absolute;
  right: 0;
  top: 0;
  width: 5%;
  height: 20px;
  font-size: 25px;
  color: #999;
}

.number {
  color: #999;
  font-size: 12px;
  margin-top: 5px;
}

.footer {
  height: 40px;
  line-height: 40px;
  width: 100%;
  text-align: center;
  margin: 50px 10px 0 10px;
  font-size: 18px;
  color: #fff;
  background-color: #333;
  border-radius: 3px;
}

.text-area {
  background-color: #333;
  color: #666;
  width: 100%;
}
</style>