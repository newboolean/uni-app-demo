<template>
	<view class="item-box">
		<view class="pic">
			<image :src="item.picurl" mode="aspectFill"></image>
		</view>
		<view class="text">
			<view class="title">{{ item.title }}</view>
			<view class="content">
				<text v-if="from === 'user'">{{ item.looktime }}</text>
				<text v-if="from === 'index'">{{ item.author }}</text>
				<text v-if="from === 'index'">{{ item.hits }}浏览</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"newItem",
		props: {
			item: {
				type: Object,
				default: () => {
					return {
						title: "标题",
						author: "作者",
						hits: 778,
						picurl: "../../static/images/itemImg.jpg",
						looktime: "2023-12-21 12:05:20"
					}
				}
			},
			from: {
				type: String,
				default: 'index'
			}
		},
		data() {
			return {
				
			};
		},
		methods: {
		}
	}
</script>

<style lang="scss" scoped>
	.item-box {
		display: flex;
		justify-content: space-between;
		.pic {
			width: 230rpx;
			height: 160rpx;
			image {
				width: 100%;
				height: 100%;
			}
		}
		.text {
			flex: 1;
			margin-left: 20rpx;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			.title {
				font-size: 36rpx;
				color: #333;
				overflow: hidden; 
			    word-break: break-all;
				-webkit-box-orient: vertical;
				display: -webkit-box;
				-webkit-line-clamp: 2;
				text-overflow: ellipsis;
			}
			.content {
				font-size: 26rpx;
				color: #999;
				display: flex;
				justify-content: space-between;
				padding-right: 20rpx;
			}
		}
	}
</style>