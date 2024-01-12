<template>
	<view class="user-box">
		<view class="top">
			<view class="img-box">
				<image src="../../static/images/user.png" mode="aspectFill"></image>
			</view>
			<view class="top-title">浏览历史</view>
		</view>
		<view class="content" v-if="historyList.length > 0">
			<view class="item" v-for="item in historyList" :key="item.id">
				<newItem from="user" :item="item" @click.native="goDetail(item)"></newItem>
			</view>
		</view>
		<view class="no-data" v-else>
			<image src="../../static/images/noData.png" mode="aspectFill"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				historyList:[]
			};
		},
		onShow() {
			this.historyList = uni.getStorageSync('newList')
		},
		methods: {
			goDetail(item) {
				uni.navigateTo({
					url:`/pages/detail/detail?cid=${item.classid}&id=${item.id}` 
				})
			}
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
	.no-data {
		margin-top: 30rpx;
		display: flex;
		justify-content: center;
	}
}
</style>
