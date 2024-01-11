<template>
  <view class="container">
    <view class="logo">
      <image class="logo-img" src="/static/images/icon/loading.gif"></image>
    </view>
    <view class="logo-name">信息维护系统</view>
    <view class="login">请完成微信授权以继续使用</view>

    <button class="btn-login" @click="getUserProfile">
      <view class="img-w"></view>
      <view class="text">微信快捷登录</view>
    </button>

    <view class="cancel" @click="goBack">取消</view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: "111"
    };
  },
  onLoad() {
    console.log("skill Launch", wx);
    wx.onAppShow(options => {
      console.log("skill AppShow");
    });
  },

  methods: {
    goBack() {
      console.log("goBack");
    },
    getUserProfile() {
      let that = this;
      let code = "";
      wx.login({
        success: res => {
          code = res.code;
        }
      });
      // 获取用户信息
      wx.getUserProfile({
        lang: "zh_CN",
        desc: "用户登录",
        success: res => {
          let loginParams = {
            code: code,
            app: 3,
            encryptedData: res.encryptedData,
            iv: res.iv,
            rawData: res.rawData,
            signature: res.signature
          };
          //TODO: 处理登录
          console.log("loginParams", loginParams);
          //存储个人信息
          // wx.setStorageSync("userInfo", res.data.userInfo);
          // wx.setStorageSync("token", res.data.token);
          wx.switchTab({
            url: "/pages/index/index"
          });
        },
        // 失败回调
        fail: () => {
          // 弹出错误
          App.showError("已拒绝小程序获取信息");
        }
      });
    }
  }
};
</script>

<style>
.container {
  background-color: #fff;
  min-height: 100%;
  align-items: stretch;
  overflow-x: hidden;
  position: relative;
  width: 100%;
  padding-top: 100rpx;
}

.logo {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 60rpx;
}

.logo .logo-img {
  width: 120rpx;
  height: 120rpx;
}

.logo-name {
  width: 100%;
  text-align: center;
  height: 50rpx;
  line-height: 50rpx;
  font-size: 32rpx;
  margin-top: 40rpx;
}

.login {
  width: 100%;
  height: 80rpx;
  margin-top: 80rpx;
  font-size: 28rpx;
  color: #999;
  text-align: center;
}

.btn-login {
  display: flex;
  justify-content: center;
  height: 100rpx;
  width: 600rpx;
  background: #54b635;
  align-items: center;
}

.img-w {
  height: 40rpx;
  width: 40rpx;
}

.text {
  font-size: 30rpx;
  color: #fff;
  margin-left: 10rpx;
}

.cancel {
  width: 100%;
  height: 100rpx;
  line-height: 100rpx;
  text-align: center;
  font-size: 28rpx;
  color: #555;
  margin-top: 30rpx;
}
</style>
