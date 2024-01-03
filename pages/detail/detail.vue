<template>
	<view class="detail">
		<view class="title">标题</view>
		<view class="info">
			<view class="author">编辑：作者</view>
			<view class="time">2023-12-25</view>
		</view>
		<view class="content">内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内容内</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad(e) {
			console.log(e)
		}
	}
</script>

<style lang="scss">
	.detail {
		padding: 30rpx;
		.title {
			font-size: 46rpx;
			color: #333333;
		}
		.info {
			background-color: #F6F6F6;
			padding: 20rpx 10rpx;
			font-size: 26rpx;
			color: #666666;
			display: flex;
			justify-content: space-between;
			margin-top: 40rpx;
		}
		.content {
			margin-top: 40rpx;
			padding-bottom: 40rpx;
		}
	}
</style>
