<template>
  <view class="page">
    <view class="header">
      <view class="header-left"
            @tap="backs">
        <text class="icon">&#xe601;</text>
      </view>
      <view class="header-content">
        组织生活
      </view>
      <view class="header-right">
        <!-- <text class="icon">&#xe622;</text> -->
      </view>
    </view>
    <view class="list">
      <view class="item"
            @tap="ways('zuzhishenghouinfo1')">
        <image src="../../static/task27.png"
               mode="" />
        党小组会
      </view>
      <view class="item"
            @tap="ways('zuzhishenghouinfo2')">
        <image src="../../static/task28.png"
               mode="" />
        支委会
      </view>
      <view class="item"
            @tap="ways('zuzhishenghouinfo3')">
        <image src="../../static/task29.png"
               mode="" />
        党课
      </view>
      <view class="item"
            @tap="ways('zuzhishenghouinfo4')">
        <image src="../../static/task30.png"
               mode="" />
        党日
      </view>
      <view class="item"
            @tap="ways('zuzhishenghouinfo5')">
        <image src="../../static/task31.png"
               mode="" />
        党员思想汇报
      </view>
      <view class="item"
            @tap="ways('zuzhishenghouinfo6')">
        <image src="../../static/task32.png"
               mode="" />
        民主评议党员
      </view>
			<view class="item"
            @tap="ways('zuzhishenghouinfo7')">
        <image src="../../static/task33.png"
               mode="" />
        支部党员大会
      </view>

    </view>
  </view>

</template>
<script>

export default {
  data () {
    return {}
  },
  methods: {
    goback: function () {
      uni.navigateBack({
        delta: 1
      })
    },
    goTo (url) {
      uni.navigateTo({
        url: url
      })
    }
  }
}
</script>
<style>
.list {
  min-height: 100px;
  width: 720px;
  margin: 30px 0 0 30px;
  overflow: hidden;
  display: flex;
  flex-wrap: wrap;
}
.item {
  width: 330px;
  height: 160px;
  background-color: #fff;
  margin: 0 30px 30px 0;
  border-radius: 12px;
	padding-left: 30px;
  box-sizing: border-box;
  font-size: 32px;
  color: #666666;
  box-shadow: 0px 4px 8px 0px #e6e6e6;
  display: flex;
  align-items: center;
  /* justify-content: center; */
}
.item image {
  width: 60px;
  height: 60px;
  margin-right: 10px;
}
</style>
