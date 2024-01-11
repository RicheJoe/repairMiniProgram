<template>
  <view class="content">
    <button @click="goPath(1)">我要上报</button>
    <button type="primary" @click="goPath(2)">我要维修</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: "Hello"
    };
  },
  onLoad() {},
  methods: {
    goPath(type) {
      switch (type) {
        case 1:
          wx.navigateTo({
            url: "/pages/submit-data/index"
          });
          break;
        case 2:
          wx.navigateTo({
            url: "/pages/repairing/index"
          });
          break;
        default:
          break;
      }
    }
  }
};
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
