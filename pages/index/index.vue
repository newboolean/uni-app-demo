<template>
	<view class="home">
		<scroll-view scroll-x class="navscroll">
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
		</scroll-view>
		<view class="content">
			<view class="item" v-for="item in 10">
				<newItem></newItem>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>
<style lang="scss" scoped>
	.navscroll {
		height: 100rpx;
		background: #F7F8FA;
		white-space: nowrap;
		position: fixed;
		top: var(--window-top);
		left: 0rpx;
		z-index: 10;
		/deep/ ::-webkit-scrollbar {
			width: 4px !important;
			height: 1px !important;
			overflow: auto !important;
			background: transparent !important;
			-webkit-appearance: auto !important;
			display: block;
		}
		.item {
			display: inline-block;
			font-size: 40rpx;
			line-height: 100rpx;
			padding: 0 40rpx;
			color: #333;
		}
	}
	.content {
		padding: 30rpx;
		padding-top: 130rpx;
		.item {
			border: 1px dashed #efefef;
			padding: 20rpx 0;
			
		}
	}
</style>
