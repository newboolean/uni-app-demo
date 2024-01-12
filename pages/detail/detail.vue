<template>
	<view class="detail">
		<view class="title">{{ detail.title }}</view>
		<view class="info">
			<view class="author">编辑：{{ detail.author }}</view>
			<view class="time">{{ retTime(detail.posttime) }}</view>
		</view>
		<view class="content">
			<rich-text :nodes="detail.content"></rich-text>
		</view>
		<view class="description">
			声明：本站的内容均采集与腾讯新闻，如果侵权请联系管理（513894357@qq.com）进行整改删除，本站进行了内容采集不代表本站及作者观点，若有侵犯请及时联系管理员，谢谢您的支持。
		</view>
	</view>
</template>

<script>
	import { parseTime } from '@/utils/tools.js'
	export default {
		data() {
			return {
			  options: null,
			  detail: {}
			};
		},
		onLoad(e) {
			this.options = e
			this.getDetail()
		},
		methods:{
			getDetail() {
				uni.request({
					url:"https://ku.qingnian8.com/dataApi/news/detail.php",
					data: this.options,
					success: (res) => {
						const content = res.data.content.replace(/<img/gi,'<img style="width: 100%"')
						res.data.content = res.data.content.replace(/<img/gi,'<img style="width: 100%"')
						this.detail = res.data
						uni.setNavigationBarTitle({
							title: this.detail.title
						})
						this.setHistory()
					}
				})
			},
			retTime(time) {
				return parseTime(time)
			},
			setHistory() {
				
				let listArr = uni.getStorageSync("newList") || []
				const item = {
					id:this.detail.id,
					classid:this.detail.classid,
					picurl:this.detail.picurl,
					title:this.detail.title,
					looktime:parseTime(Date.now())
				}
				const index = listArr.findIndex(e => e.id === item.id)
				if(index > -1) {
					listArr.splice(index,1)
				}
				listArr.unshift(item)
				uni.setStorageSync('newList',listArr)
			}
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
		.description{
			background: #FEF0F0;
			font-size: 26rpx;
			padding:20rpx;
			color:#F89898;
			line-height: 1.8em;
		}
	}
</style>
