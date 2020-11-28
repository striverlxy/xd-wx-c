<template>
	<view class="container">
		<home />
		<!--tabbar-->
		<view class="tui-tabbar">
			<block v-for="(item, index) in tabbar" :key="index">
				<view class="tui-tabbar-item" :class="[current == index ? 'tui-item-active' : '']" :data-index="index" @tap="tabbarSwitch">
					<view :class="[index == 0 ? 'tui-ptop-4' : '']">
						<tui-icon :name="current == index ? item.icon + '-fill' : item.icon" :color="current == index ? '#E41F19' : '#666'"
						 :size="item.size" unit="rpx"></tui-icon>
					</view>
					<view class="tui-scale">{{ item.text }}</view>
				</view>
			</block>
		</view>
	</view>
</template>

<script>
	
	import home from '../home/home.vue'
	
	export default {
		components: {home},
		data() {
			return {
				current: 0,
				tabbar: [{
						icon: 'home',
						text: '首页',
						size: 48
					},
					{
						icon: 'manage',
						text: '分类',
						size: 54
					},
					{
						icon: 'cart',
						text: '购物车',
						size: 48
					},
					{
						icon: 'people',
						text: '我的',
						size: 52
					}
				],
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	page {
		background-color: #f7f7f7;
	}

	.container {
		padding-bottom: 100rpx;
		color: #333;
	}

	/*tabbar*/

	.tui-tabbar {
		width: 100%;
		position: fixed;
		display: flex;
		align-items: center;
		justify-content: space-between;
		z-index: 99999;
		background: #fff;
		height: 100rpx;
		left: 0;
		bottom: 0;
		padding-bottom: env(safe-area-inset-bottom);
	}

	.tui-safearea-bottom {
		width: 100%;
		height: env(safe-area-inset-bottom);
	}

	.tui-tabbar::before {
		content: '';
		width: 100%;
		border-top: 1rpx solid #d9d9d9;
		position: absolute;
		top: 0;
		left: 0;
		-webkit-transform: scaleY(0.5);
		transform: scaleY(0.5);
	}

	.tui-tabbar-item {
		flex: 1;
		width: 25%;
		display: flex;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		font-size: 24rpx;
		color: #666;
		height: 80rpx;
	}
	
	/* home页面轮播图更改样式 start */
	
	/* #ifdef MP-WEIXIN */
	.tui-banner-swiper .wx-swiper-dot {
		width: 8rpx;
		height: 8rpx;
		display: inline-flex;
		background: none;
		justify-content: space-between;
	}
	
	.tui-banner-swiper .wx-swiper-dot::before {
		content: '';
		flex-grow: 1;
		background-color: rgba(255, 255, 255, 0.8);
		border-radius: 16rpx;
		overflow: hidden;
	}
	
	.tui-banner-swiper .wx-swiper-dot-active::before {
		background-color: #fff;
	}
	
	.tui-banner-swiper .wx-swiper-dot.wx-swiper-dot-active {
		width: 16rpx;
	}
	/* #endif */
	
	/* #ifndef MP-WEIXIN */
	>>>.tui-banner-swiper .uni-swiper-dot {
		width: 8rpx;
		height: 8rpx;
		display: inline-flex;
		background-color: none;
		justify-content: space-between;
	}
	
	>>>.tui-banner-swiper .uni-swiper-dot::before {
		content: '';
		flex-grow: 1;
		background-color: rgba(255, 255, 255, 0.8);
		border-radius: 16rpx;
		overflow: hidden;
	}
	
	>>>.tui-banner-swiper .uni-swiper-dot-active::before {
		background-color: #fff;
	}
	
	>>>.tui-banner-swiper .uni-swiper-dot.uni-swiper-dot-active {
		width: 16rpx;
	}
	
	/* #endif */
	/* home页面轮播图更改样式 end */
</style>
