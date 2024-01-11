<template>
  <view class="content">
    <view class="text-area">
      <text class="title">{{ ucenter }}</text>
    </view>
    <p>ucenterucenterucenterucenterucenter</p>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: "ucenter"
    };
  },
  onLoad() {
    console.log("ucenter Launch", wx);
    wx.onAppShow(options => {
      console.log("ucenter AppShow");
    });
  },

  methods: {}
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
