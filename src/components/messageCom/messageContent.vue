<template>
  <view class="msg-content">
    <view class="box">
      <view class="icon">
        <view class="box-img">
          <view class="iconfont icon-fensi img"></view>
        </view>
        <view class="icon-text">
          粉丝
        </view>
      </view>
      <view class="icon">
        <view class="box-img">
          <view class="iconfont icon-dianzan img"></view>
        </view>
        <view class="icon-text">
          点赞
        </view>
      </view>
      <view class="icon">
        <view class="box-img">
          <view class="iconfont icon-pinglun1 img"></view>
        </view>
        <view class="icon-text">
          评论和@
        </view>
      </view>
      <view class="icon">
        <view class="box-img">
          <view class="iconfont icon-suipaihudong img"></view>
        </view>
        <view class="icon-text">
          随拍互动
        </view>
      </view>
    </view>
    <view class="line"></view>
    <view class="msg-list">
      <view class="item" v-for="(item,index) of list" :key="index">
        <view class="author-img-box">
          <image class="author-img" :src='item.authorImg'></image>
        </view>
        <view class="text">
          <view class="top">
            <view class="name">{{item.authorName}}</view>
            <view class="date">{{item.date}}</view>
          </view>
          <view class="content">
            {{item.content}}
          </view>
        </view>
      </view>
      <view class="more">
        无更多消息
      </view>
    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {
      list: [
        {
          authorImg: '../../static/img/avatar.jpg',
          authorName: 'czd',
          date: '星期一',
          content: 'hello,world!',
        },
        {
          authorImg: '../../static/img/around.jpg',
          authorName: 'cxx',
          date: '星期一',
          content: 'I’m fw !',
        },
        {
          authorImg: '../../static/img/avatar.jpg',
          authorName: 'zkw',
          date: '星期二',
          content: 'I’m trash !',
        },
        {
          authorImg: '../../static/img/around.jpg',
          authorName: 'x9',
          date: '星期二',
          content: 'I’m 9 爷!',
        },
      ],
    }
  },
}
</script>
<style >
.msg-content {
  width: 100%;
  background-color: #000;
}
.box {
  width: 100%;
  height: 120px;
}

.icon {
  width: 25%;
  height: 100px;
  float: left;
  margin: 0 auto;
}

.box-img {
  text-align: center;
}

.img {
  text-align: center;
  border-radius: 5px;
  margin-top: 20px;
  color: pink;
  font-size: 25px;
}

.icon-text {
  font-size: 15px;
  text-align: center;
  color: #eee;
  margin-top: 10px;
}

.msg-list {
  background-color: #000;
}
.item {
  height: 60px;
  padding: 15px 10px;
}

.author-img-box {
  float: left;
  margin-left: 10px;
}

.author-img {
  width: 45px;
  height: 45px;
  border-radius: 50%;
}

.text {
  float: left;
  margin-left: 15px;
  height: 50px;
  width: 75%;
  color: #fff;
}

.top {
  height: 25px;
  line-height: 25px;
}

.name {
  float: left;
  font-size: 18px;
}

.date {
  float: right;
  font-size: 11px;
  color: #aaa;
}
.content {
  height: 25px;
  line-height: 25px;
  font-size: 13px;
  color: #aaa;
}

.more {
  width: 100%;
  height: 50px;
  line-height: 50px;
  font-size: 12px;
  text-align: center;
  color: #aaa;
}

.line {
  width: 100%;
  height: 0.5px;
  background-color: #666;
  transform: scaleY(0.5);
  transform-origin: 50% 100%;
}
</style>