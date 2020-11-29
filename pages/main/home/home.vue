<template>
	<view>
		<view class="tui-header" :style="{opacity:opacity}">
			<view class="location">
				<tui-icon class="mgr-10" name="gps" color="#fff" :size="30" unit="rpx"></tui-icon>
				<view class="mgr-10">梅山村邱村69号</view>
				<view>></view>
			</view>
			<view class="tui-rolling-search">
				<tui-icon name="search-2" :size="32" unit="rpx"></tui-icon>
				<swiper vertical autoplay circular interval="8000" class="tui-swiper">
					<swiper-item v-for="(item, index) in hotSearch" :key="index" class="tui-swiper-item" @tap="search">
						<view class="tui-hot-item">{{ item }}</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		<!--header-->
		<view class="tui-header-banner">
			<view class="platform-service">
				<view class="service-tag">农场直供</view>
				<view class="service-tag">新鲜速达</view>
				<view class="service-tag">零差价</view>
				<view class="service-tag">精心挑选</view>
			</view>
			<view class="tui-banner-bg">
				<view class="tui-primary-bg tui-route-left"></view>
				<view class="tui-primary-bg tui-route-right"></view>
				<!--banner-->
				<view class="tui-banner-box">
					<swiper :indicator-dots="true" :autoplay="true" :interval="5000" :duration="150" class="tui-banner-swiper"
					 :circular="true" indicator-color="rgba(255, 255, 255, 0.8)" indicator-active-color="#fff">
						<swiper-item v-for="(item, index) in banner" :key="index" @tap.stop="detail">
							<image :src="'https://thorui.cn/images/mall/banner/' + item" class="tui-slide-image" mode="scaleToFill" />
						</swiper-item>
					</swiper>
				</view>
			</view>
		</view>
		
		<view class="special-page">
			<view class="special-page-item" v-for="(item, index) in category" :key="index" :data-key="item.name" @tap="more">
				<image :src="'https://thorui.cn/images/mall/category/' + item.img" class="special-page-img" mode="scaleToFill"></image>
				<view class="special-page-name">{{ item.name }}</view>
			</view>
		</view>
		
		<view class="tui-product-box">
			<view class="tui-title__img">
				<image src="https://thorui.cn/images/mall/img_home_update_3x.png" mode="widthFix"></image>
			</view>
			<view class="tui-product-list">
				<view class="tui-product-container">
					<template v-for="(item, index) in productList">
						<block  :key="index" v-if="(index + 1) % 2 != 0">
							<!--商品列表-->
							<view class="tui-pro-item" hover-class="hover" :hover-start-time="150" @tap="detail">
								<image :src="'/static/images/mall/product/' + item.img + '.jpg'" class="tui-pro-img" mode="widthFix" />
								<view class="tui-pro-content">
									<view class="tui-pro-tit">{{ item.name }}</view>
									<view>
										<view class="tui-pro-price">
											<text class="tui-sale-price">￥{{ item.sale }}</text>
											<text class="tui-factory-price">￥{{ item.factory }}</text>
										</view>
										<view class="tui-pro-pay">{{ item.payNum }}人付款</view>
									</view>
								</view>
							</view>
							<!--商品列表-->
							<!-- <template is="productItem" data="{{item,index:index}}" /> -->
						</block>
					</template>
				</view>
				<view class="tui-product-container">
					<template v-for="(item, index) in productList">
						<block :key="index" v-if="(index + 1) % 2 == 0">
							<!--商品列表-->
							<view class="tui-pro-item" hover-class="hover" :hover-start-time="150" @tap="detail">
								<image :src="'/static/images/mall/product/' + item.img + '.jpg'" class="tui-pro-img" mode="widthFix" />
								<view class="tui-pro-content">
									<view class="tui-pro-tit">{{ item.name }}</view>
									<view>
										<view class="tui-pro-price">
											<text class="tui-sale-price">￥{{ item.sale }}</text>
											<text class="tui-factory-price">￥{{ item.factory }}</text>
										</view>
										<view class="tui-pro-pay">{{ item.payNum }}人付款</view>
									</view>
								</view>
							</view>
							<!--商品列表-->
						</block>
					</template>
				</view>
			</view>
		</view>
		
		<!--加载loadding-->
		<tui-loadmore v-if="loadding" :index="3" type="red"></tui-loadmore>
		<!-- <tui-nomore v-if="!pullUpOn"></tui-nomore> -->
		<!--加载loadding-->
		<view class="tui-safearea-bottom"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				hotSearch: ['休闲零食', '自热火锅', '小冰箱迷你'],
				banner: ['1.jpg', '2.jpg', '3.jpg', '4.jpg', '5.jpg'],
				category: [{
						img: '1.png',
						name: '健康饮食'
					},
					{
						img: '2.png',
						name: '为您优选'
					},
					{
						img: '3.png',
						name: '瘦身食材'
					},
					{
						img: '4.png',
						name: '鲜道服务'
					}
				],
				productList: [{
						img: 1,
						name: '欧莱雅（LOREAL）奇焕光彩粉嫩透亮修颜霜 30ml（欧莱雅彩妆 BB霜 粉BB 遮瑕疵 隔离）',
						sale: 599,
						factory: 899,
						payNum: 2342
					},
					{
						img: 2,
						name: '德国DMK进口牛奶  欧德堡（Oldenburger）超高温处理全脂纯牛奶1L*12盒',
						sale: 29,
						factory: 69,
						payNum: 999
					},
					{
						img: 3,
						name: '【第2支1元】柔色尽情丝柔口红唇膏女士不易掉色保湿滋润防水 珊瑚红',
						sale: 299,
						factory: 699,
						payNum: 666
					},
					{
						img: 4,
						name: '百雀羚套装女补水保湿护肤品',
						sale: 1599,
						factory: 2899,
						payNum: 236
					}
				],
				pageIndex: 1,
				loadding: false,
				pullUpOn: true,
				opacity: 1
			}
		},
		methods: {
			search() {
				uni.navigateTo({
					url: "/pages/pages-home/pages/search/search"
				})
			},
		},
	}
</script>

<style>
	.tui-safearea-bottom {
		width: 100%;
		height: env(safe-area-inset-bottom);
	}
	.tui-header {
		width: 100%;
		height: 100rpx;
		padding: 0 30rpx 0 20rpx;
		box-sizing: border-box;
		background-color: #e41f19;
		display: flex;
		align-items: center;
		justify-content: space-between;
		position: fixed;
		left: 0;
		top: 0;
		/* #ifdef H5 */
		top: 44px;
		/* #endif */
		z-index: 999;
		transition: opacity .4s;
	}
	.tui-rolling-search {
		width: 100%;
		height: 60rpx;
		border-radius: 35rpx;
		padding: 0 40rpx 0 30rpx;
		box-sizing: border-box;
		background-color: #fff;
		display: flex;
		align-items: center;
		flex-wrap: nowrap;
		color: #999;
	}
	
	.mgr-10 {
		margin-right: 10rpx;
	}
	.location {
		font-size: 24rpx;
		color: #fff;
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0;
		margin-right: 22rpx;
		flex-shrink: 0;
	}
	
	.tui-category-scale {
		transform: scale(0.7);
		line-height: 24rpx;
	}
	
	.tui-icon-category {
		line-height: 20px !important;
		margin-bottom: 0 !important;
	}
	.tui-swiper {
		font-size: 26rpx;
		height: 60rpx;
		flex: 1;
		padding-left: 12rpx;
	}
	
	.tui-swiper-item {
		display: flex;
		align-items: center;
	}
	
	.tui-hot-item {
		line-height: 26rpx;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	
	.tui-header-banner {
		padding-top: 100rpx;
		box-sizing: border-box;
		background: #e41f19;
	}
	
	.platform-service {
		color: #fff;
		font-size: 24rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 20rpx;
		box-sizing: border-box;
		position: relative;
		z-index: 2;
	}
	
	.service-tag {
		background-color: rgba(255, 255, 255, 0.15);
		padding: 10rpx 24rpx;
		border-radius: 30rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		line-height: 24rpx;
	}
	
	.tui-banner-bg {
		display: flex;
		height: 180rpx;
		background-color: #e41f19;
		position: relative;
	}
	
	.tui-primary-bg {
		width: 50%;
		display: inline-block;
		height: 224rpx;
		border: 1px solid transparent;
		position: relative;
		z-index: 1;
		background-color: #e41f19;
	}
	
	.tui-route-left {
		transform: skewY(8deg);
	}
	
	.tui-route-right {
		transform: skewY(-8deg);
	}
	
	.tui-banner-box {
		width: 100%;
		padding: 0 20rpx;
		box-sizing: border-box;
		position: absolute;
		/* overflow: hidden; */
		z-index: 99;
		bottom: -80rpx;
		left: 0;
	}
	
	.tui-banner-swiper {
		width: 100%;
		height: 240rpx;
		border-radius: 20rpx;
		overflow: hidden;
		transform: translateY(0);
		background-color: #f8f8f8;
	}
	
	.tui-slide-image {
		width: 100%;
		height: 240rpx;
		display: block;
	}
	
	.special-page {
		padding: 80rpx 20rpx 30rpx 20rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		font-size: 24rpx;
		color: #555;
		/* margin-bottom: 20rpx; */
	}
	
	.special-page-item {
		width: 20%;
		height: 118rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-direction: column;
		padding-top: 30rpx;
	}
	
	.special-page-img {
		height: 80rpx;
		width: 80rpx;
		display: block;
	}
	
	.special-page-name {
		line-height: 24rpx;
	}
	.tui-product-box {
		margin-top: 20rpx;
		padding: 0 25rpx;
		box-sizing: border-box;
	}
	.tui-title__img {
		width: 100%;
		padding: 30rpx 0;
		display: flex;
		justify-content: center;
	}
	
	.tui-title__img image {
		width: 352rpx;
		height: 32rpx;
	}
	
	.tui-product-list {
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		flex-wrap: wrap;
		box-sizing: border-box;
		/* padding-top: 20rpx; */
	}
	
	.tui-product-container {
		flex: 1;
		margin-right: 2%;
	}
	
	.tui-product-container:last-child {
		margin-right: 0;
	}
	
	.tui-pro-item {
		width: 100%;
		margin-bottom: 4%;
		background: #fff;
		box-sizing: border-box;
		border-radius: 12rpx;
		overflow: hidden;
	}
	
	.tui-pro-img {
		width: 100%;
		display: block;
	}
	
	.tui-pro-content {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		box-sizing: border-box;
		padding: 20rpx;
	}
	
	.tui-pro-tit {
		color: #2e2e2e;
		font-size: 26rpx;
		word-break: break-all;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}
	
	.tui-pro-price {
		padding-top: 18rpx;
	}
	
	.tui-sale-price {
		font-size: 34rpx;
		font-weight: 500;
		color: #e41f19;
	}
	
	.tui-factory-price {
		font-size: 24rpx;
		color: #a0a0a0;
		text-decoration: line-through;
		padding-left: 12rpx;
	}
	
	.tui-pro-pay {
		padding-top: 10rpx;
		font-size: 24rpx;
		color: #656565;
	}
</style>
