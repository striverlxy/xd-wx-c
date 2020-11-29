<template>
	<view>
		<view class="location">
			<view class="address">
				<tui-icon class="mgr-10" name="gps" color="#fff" :size="30" unit="rpx"></tui-icon>南京市雨花台区梅山村邱村69号
			</view>
			<view>
				更换地址 >
			</view>
		</view>
		<view class="header">
			<view class="tui-searchbox">
				<view class="tui-search-input">
					<icon type="search" :size='13' color='#333'></icon>
					<input confirm-type="search" placeholder="大家都在搜：2019退役球星" :focus="true" auto-focus placeholder-class="tui-input-plholder"
					 class="tui-input" v-model.trim="key" @input="inputKey"/>
					<icon type="clear" :size='13' color='#bcbcbc' @tap="cleanKey" v-show="key"></icon>
				</view>
			</view>
		</view>
		<!--list-->
		<view class="tui-product-list">
			<view class="tui-product-container">
				<block v-for="(item, index) in productList" :key="index">
					<!--商品列表-->
					<view class="tui-pro-item tui-flex-list" hover-class="tui-hover" :hover-start-time="150" @tap="detail">
						<image :src="'/static/images/mall/product/' + item.img + '.jpg'" class="tui-pro-img tui-proimg-list" mode="widthFix" />
						<view class="tui-pro-content">
							<view class="tui-pro-tit"><tui-tag v-if="index == 0" margin="0 10rpx 0 0" padding="5rpx" size="16rpx" type="danger">最近</tui-tag>{{ item.name }}</view>
							<view>
								<view class="tui-pro-price">
									<text class="tui-sale-price">配送时间 07:00 ~ 21:30</text>
								</view>
								<view class="tui-pro-pay">站点地址：南京市雨花台区梅山村邱村96号</view>
							</view>
						</view>
					</view>
					<!--商品列表-->
				</block>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				productList: [
					{
						img: 1,
						name: '南京市雨花台区板桥站点',
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
					},
					{
						img: 5,
						name: '百草味 肉干肉脯 休闲零食 靖江精制猪肉脯200g/袋',
						sale: 599,
						factory: 899,
						payNum: 2399
					},
					{
						img: 6,
						name: '短袖睡衣女夏季薄款休闲家居服短裤套装女可爱韩版清新学生两件套 短袖粉色长颈鹿 M码75-95斤',
						sale: 599,
						factory: 899,
						payNum: 2399
					},
					{
						img: 1,
						name: '欧莱雅（LOREAL）奇焕光彩粉嫩透亮修颜霜',
						sale: 599,
						factory: 899,
						payNum: 2342
					},
					{
						img: 2,
						name: '德国DMK进口牛奶',
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
			}
		}
	}
</script>

<style>
	page {
		background-color: #f7f7f7;
	}
	
	.mgr-10 {
		margin-right: 10rpx;
	}
	.location {
		width: 100%;
		padding: 18rpx 30rpx;
		box-sizing: border-box;
		position: fixed;
		display: flex;
		justify-content: space-between;
		align-items: center;
		z-index: 9999;
		color: #fff;
		background: #52c41a;
		font-size: 21rpx;
		left: 0;
		top: 0;
	}
	.address {
		display: flex;
		align-items: center;
	}
	
	.header {
		margin-top: 60rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		background: #FFFFFF;
	}
	
	.tui-searchbox {
		margin: 0 30rpx;
		padding: 30rpx 0;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		background: #FFFFFF;
	}
	
	.tui-search-input {
		width: 100%;
		height: 66rpx;
		border-radius: 35rpx;
		padding: 0 30rpx;
		box-sizing: border-box;
		background: #f2f2f2;
		display: flex;
		align-items: center;
		flex-wrap: nowrap;
	}
	
	.tui-input {
		flex: 1;
		color: #333;
		padding: 0 16rpx;
		font-size: 28rpx;
	}
	
	.tui-input-plholder {
		font-size: 28rpx;
		color: #b2b2b2;
	}
	
	.tui-cancle {
		color: #888;
		font-size: 28rpx;
		padding-left: 30rpx;
		flex-shrink: 0;
	}
	/* 商品列表*/
	
	.tui-product-list {
		margin-top: 20rpx;
		display: flex;
		justify-content: space-between;
		flex-direction: row;
		flex-wrap: wrap;
		box-sizing: border-box;
	}
	
	.tui-product-container {
		flex: 1;
		margin-right: 10rpx;
	}
	
	.tui-product-container:last-child {
		margin-right: 0;
	}
	
	.tui-pro-item {
		padding: 0 30rpx;
		width: 100%;
		margin-bottom: 10rpx;
		background: #fff;
		box-sizing: border-box;
		border-radius: 12rpx;
		overflow: hidden;
		transition: all 0.15s ease-in-out;
	}
	
	.tui-flex-list {
		display: flex;
		margin-bottom: 1rpx !important;
	}
	
	.tui-pro-img {
		width: 100%;
		display: block;
	}
	
	.tui-proimg-list {
		width: 180rpx;
		height: 180rpx !important;
		flex-shrink: 0;
		border-radius: 12rpx;
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
/* 		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2; */
		display: flex;
		/* justify-content: center; */
		align-items: center;
	}
	
	.tui-pro-price {
		padding-top: 18rpx;
	}
	
	.tui-sale-price {
		color: #b2b2b2;
		font-size: 20rpx
	}
	
	.tui-factory-price {
		font-size: 24rpx;
		color: #a0a0a0;
		text-decoration: line-through;
		padding-left: 12rpx;
	}
	
	.tui-pro-pay {
		padding-top: 10rpx;
		color: #b2b2b2;
		font-size: 20rpx
	}
	/* 商品列表*/
</style>
