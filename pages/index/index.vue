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
			没一行的内容
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
</style>
