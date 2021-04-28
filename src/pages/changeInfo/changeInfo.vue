<template>
  <view class="change-info">
    <view class="nav-box">
      <view class="title">
        编辑个人资料
      </view>
      <navigator open-type='switchTab' url='/pages/personal/personal' class="iconfont icon-back icon-nav"></navigator>
    </view>
    <view class="box">
      <view class="img-box">
        <image class="img" :src='src' @click="chooseImg"></image>
        <view class="text">点击更换头像</view>
      </view>
    </view>
    <view class="info-box">
      <view class="text-box" @click="goModify('昵称',user.username)">
        <view class="left">
          昵称
        </view>
        <view class="iconfont icon-right icon-box"></view>
        <view class="right">
          {{user.username}}
        </view>
      </view>
      <view class="text-box" @click="goModify('抖音号',123456)">
        <view class="left">
          抖音号
        </view>
        <view class="iconfont icon-right icon-box"></view>
        <view class="right">
          {{user.userId}}
        </view>
      </view>
      <view class="text-box" @click="goModify('简介','我爱学习')">
        <view class="left">
          简介
        </view>
        <view class="iconfont icon-right icon-box"></view>
        <view class="right">
          {{user.content}}
        </view>
      </view>
      <picker class="school" :range='school' @change="changeSchool">
        <view class="text-box">
          <view class="left">
            学校
          </view>
          <view class=" iconfont icon-right icon-box">
          </view>
          <view class="right">
            {{user.school}}
          </view>
        </view>
      </picker>
      <picker class="gender" :range='gender' @change="changeGender">
        <view class="text-box">
          <view class="left">
            性别
          </view>
          <view class=" iconfont icon-right icon-box">
          </view>
          <view class="right">
            {{user.gender}}
          </view>
        </view>
      </picker>

      <picker class="gender" mode='date' :value='user.birthday' @change="changeDate">
        <view class="text-box">
          <view class="left">
            生日
          </view>
          <view class="iconfont icon-right icon-box"></view>
          <view class="right">
            {{user.birthday}}
          </view>
        </view>
      </picker>

      <picker class="region" mode='region' :value='user.region' @change="changeRegion">
        <view class="text-box">
          <view class="left">
            地区
          </view>
          <view class="iconfont icon-right icon-box"></view>
          <view class="right">
            {{user.region}}
          </view>
        </view>
      </picker>

    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {
      src: '../../static/img/avatar.jpg',
      user: {
        username: 'czd',
        userId: '123456',
        content: '我爱学习',
        school: '大学',
        gender: '点击选择性别',
        region: '广东省',
        birthday: '1999-03-12',
      },
      school: ['清华大学', '北京大学', '复旦大学', '深圳大学', '中山大学'],
      gender: ['男', '女'],
    }
  },
  methods: {
    chooseImg() {
      uni.chooseImage({
        count: 1,
        souceType: ['album'],
        sizeType: ['original', 'compressed'],
        success: (res) => {
          this.src = res.tempFilePaths
        },
      })
    },
    goModify(title, value) {
      uni.redirectTo({
        url: '/pages/modify/modify?title=' + title + '&value=' + value,
      })
    },
    changeSchool(e) {
      this.user.school = this.school[e.target.value]
      uni.setStorage({
        key: 'school',
        data: this.school[e.target.value],
      })
    },
    changeGender(e) {
      this.user.gender = this.gender[e.target.value]
      uni.setStorage({
        key: 'gender',
        data: this.gender[e.target.value],
      })
    },
    changeRegion(e) {
      this.user.region = e.target.value
      uni.setStorage({
        key: 'region',
        data: e.target.value,
      })
    },
    changeDate(e) {
      this.user.birthday = e.target.value
      uni.setStorage({
        key: 'birthday',
        data: e.target.value,
      })
    },
  },
  onLoad() {
    uni.getStorage({
      key: 'username',
      success: (res) => {
        this.user.username = res.data
      },
    })
    uni.getStorage({
      key: 'userId',
      success: (res) => {
        this.user.userId = res.data
      },
    })
    uni.getStorage({
      key: 'content',
      success: (res) => {
        this.user.content = res.data
      },
    })
    uni.getStorage({
      key: 'school',
      success: (res) => {
        this.user.school = res.data
      },
    })
    uni.getStorage({
      key: 'gender',
      success: (res) => {
        this.user.gender = res.data
      },
    })
    uni.getStorage({
      key: 'region',
      success: (res) => {
        this.user.region = res.data
      },
    })
    uni.getStorage({
      key: 'birthday',
      success: (res) => {
        this.user.birthday = res.data
      },
    })
  },
}
</script>
<style >
.change-info {
  height: 100%;
  width: 100%;
  background-color: #000;
}

.nav-box {
  height: 50px;
  position: relative;
  margin: 0 auto;
  padding-top: 30px;
}

.title {
  text-align: center;
  color: #fff;
  font-size: 18px;
}

.icon-nav {
  position: absolute;
  top: 35px;
  color: #fff;
  left: 10px;
}

.box {
  width: 100%;
  height: 150px;
  margin: 0 auto;
  border-top: 1px solid #333;
  border-bottom: 1px solid #333;
}

.img-box {
  text-align: center;
}

.img {
  margin-top: 20px;
  width: 70px;
  height: 70px;
  border-radius: 50%;
}

.text {
  margin-top: 13px;
  color: #999;
  font-size: 13px;
}

.info-box {
  padding: 0 10px;
}

.text-box {
  width: 100%;
  height: 52px;
  line-height: 52px;
}

.left {
  float: left;
  font-size: 15px;
  color: #fff;
}

.right {
  float: right;
  font-size: 15px;
  margin-right: 7px;
  color: #999;
}

.icon-box {
  float: right;
  font-size: 15px;
  color: #999;
  width: 10px;
}
</style>