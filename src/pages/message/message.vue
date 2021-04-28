<template>
  <view class="message">
    <message-nav class=""></message-nav>
    <message-content class="msg-content"></message-content>
    <tab-bar></tab-bar>
  </view>
</template>
<script>
import messageNav from '../../components/messageCom/messageNav'
import tabBar from '../../components/tab'
import messageContent from '../../components/messageCom/messageContent'

export default {
  components: {
    messageNav,
    tabBar,
    messageContent,
  },
}
</script>
<style >
.message {
  width: 100%;
  height: 100%;
  background-color: #000;
}
</style>