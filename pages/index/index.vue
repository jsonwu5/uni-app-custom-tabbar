<template>
	<view class="app">
		<page text="A" v-if="PageCur == 'index'" color="white"></page>
		<page text="B" v-if="PageCur == 'category'" color="red"></page>
		<page text="C" v-if="PageCur == 'cart'" color="blue"></page>
		<page text="D" v-if="PageCur == 'user'" color="yellow"></page>
		<page text="E" v-if="PageCur == 'diypage'" color="green"></page>
		<view class="cu-bar tabbar bg-white shadow foot" v-if="tabbar.length > 0">
			<view class="action" @click="NavChange(item)" :data-cur="item.isSystem" v-for="(item, index) in tabbar" :key="index">
				<view class="cuIcon-cu-image">
					<image class="image" :src="item.imageUrl"></image>
				</view>
				<view :class="item.indexCur == indexCur ? 'text-select' : 'text-normal'">{{ item.name }}</view>
			</view>
		</view>
	</view>
</template>

<script>
import page from "@/components/page.vue";
export default {
  components: {
    page
  },
  data() {
      return {
        PageCur: "index", // 当前页面类型
        indexCur: 0, // 当前页面下标 默认为第一个
        tabbar: [
          {
						name: "首页",
						isShow: true,
						iconId: "2a78cfc4-d8ad-1485-a64d-39f34aaac5b6",
						imageUrl: "https://s2.ax1x.com/2020/02/21/3nbw1s.png",
						target: "",
						targetId: 0,
						indexCur: 0,
						isSystem: "index"
					},
					{
						name: "分类",
						isShow: true,
						iconId: "605b94c4-324f-0c3f-f002-39f34aaae633",
						imageUrl: "https://s2.ax1x.com/2020/02/21/3nbdpj.png",
						target: "",
						targetId: 0,
						indexCur: 1,
						isSystem: "category"
					},
					{
						name: "购物车",
						isShow: true,
						iconId: "b3f58662-39dd-e6fa-0674-39f34aaafbdb",
						imageUrl: "https://s2.ax1x.com/2020/02/21/3nbUhQ.png",
						target: "",
						targetId: 0,
						indexCur: 2,
						isSystem: "cart"
					},
					{
						name: "我的",
						isShow: true,
						iconId: "c69cc52c-db0e-bddf-291e-39f34aab1c41",
						imageUrl: "https://s2.ax1x.com/2020/02/21/3nbNtg.png",
						target: "",
						targetId: 0,
						indexCur: 3,
						isSystem: "user"
					}
        ]
      };
    },
    computed: {
      // 当前选择的item数据
      cuItem() {
        if (this.tabbar && this.tabbar.length > 0) {
          return this.tabbar[this.indexCur];
        }
        return {};
      }
    },
    methods: {
      NavChange: function(item) {
        console.log(item);
        this.PageCur = item.isSystem;
        this.indexCur = item.indexCur;
      }
    }
}
</script>

<style>
page, #app {
	height: 100%;
	width: 100%;
	padding: 0;
}
</style>
<style lang="scss">
bodey,
.page,
page
.app {
  height: 100%;
  width: 100%;
  padding: 0;
}
.cu-bar {
  display: flex;
  position: relative;
  align-items: center;
  min-height: 100rpx;
  justify-content: space-between;
  &.bg-white {
    background-color: #ffffff;
    color: #666666;
  }
  &.tabbar {
    padding: 0;
    height: calc(100rpx + env(safe-area-inset-bottom) / 2);
    padding-bottom: calc(env(safe-area-inset-bottom) / 2);
    &.shadow {
      box-shadow: 0 -1rpx 6rpx rgba(0, 0, 0, 0.1);
    }
    .action {
      font-size: 22rpx;
      position: relative;
      flex: 1;
      text-align: center;
      padding: 0;
      display: block;
      height: auto;
      line-height: 1;
      margin: 0;
      background-color: inherit;
      overflow: initial;
      .text-select {
        color: #fa436a;
      }
      .text-normal {
        color: #c0c4cc;
      }
      [class*="cuIcon-"] {
        width: 50rpx;
        position: relative;
        display: block;
        height: auto;
        margin: 0 auto 10rpx;
        text-align: center;
        font-size: 40rpx;
      }
    }
  }
  .cuIcon-cu-image {
    margin: 0 auto;
    .image {
      max-width: 100%;
      position: relative;
      z-index: 0;
      width: 50rpx;
      height: 50rpx;
      display: inline-block;
    }
  }
  &.foot {
    position: fixed;
    width: 100%;
    bottom: 0;
    z-index: 998;
    box-shadow: 0 -1rpx 6rpx rgba(0, 0, 0, 0.1);
  }
}
</style>