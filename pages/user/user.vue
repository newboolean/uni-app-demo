<template>
	<view class="user-box">
		<view class="top">
			<view class="img-box">
				<image src="../../static/images/nock.jpg" mode="aspectFill"></image>
			</view>
			<view class="top-title">浏览历史</view>
		</view>
		<view class="content">
			<view class="item">
				<newItem></newItem>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
.user-box {
	.top {
		background: #F8F8F8;
		display: flex;
		justify-content: space-between;
		flex-direction: column;
		align-items: center;
		padding: 50rpx 0;
		.img-box {
			width: 300rpx;
			height: 300rpx;
			overflow: hidden;
			border-radius: 50%;
		}
		.top-title {
			margin-top: 20rpx;
			text-align: center;
			font-size: 40rpx;
			color: #666;
		}
	}
	.content {
		padding: 30rpx;
		.item {
			border: 1px dashed #efefef;
			padding: 20rpx 0;
			
		}
	}
}
</style>
