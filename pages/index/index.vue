<template>
	<view class="home">
		<scroll-view scroll-x class="navscroll">
			<view
				class="item"
				v-for="(item,index) in navList"
				:key="item.id"
				:class="index === navIndex ? 'active' : ''"
				@click="changeNav(index,item.id)"
			>
				{{ item.classname }}
			</view>
		</scroll-view>
		<view class="content">
			<view class="item" v-for="item in newList" :key="item.id">
				<newItem :item="item" @click.native="goDetail(item)"></newItem>
			</view>
		</view>
		<view class="no-data" v-if="newList.length === 0">
			<image src="../../static/images/noData.png" mode="aspectFill"></image>
		</view>
		<view class="loading" v-if="newList.length > 0">
			<view></view>
			<view v-if="loading === 1">数据加载中</view>
			<view v-if="loading === 2">没有更多数据了</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList: [],
				newList: [],
				navIndex: 0,
				currentNav: '',
				currentPage: 1,
				loading: 0 // 0默认 1加载中 2没有更多
			}
		},
		onLoad() {
			this.getNavData()
			this.getNewList()
		},
		onReachBottom() {
			if(this.loading !== 2) {
				this.currentPage++
				this.loading = 1
				this.getNewList()
			}
		},
		methods: {
			// 调整详情页
			goDetail(item) {
				uni.navigateTo({
					url:`/pages/detail/detail?cid=${item.classid}&id=${item.id}` 
				})
			},
			changeNav(index,id) {
				this.navIndex = index
				this.currentNav = id
				this.currentPage = 1
				this.loading = 0
				this.newList = []
				this.getNewList()
			},
			getNavData() {
				uni.request({
					url:'https://ku.qingnian8.com/dataApi/news/navlist.php',
					success: res => {
						this.navList = res.data
					}
				})
			},
			getNewList() {
				uni.request({
					url:'https://ku.qingnian8.com/dataApi/news/newslist.php',
					data: {
						cid: this.currentNav,
						page: this.currentPage
					},
					success: res =>{
						if(res.data.length === 0) {
							this.loading = 2
						}
						this.newList = [...this.newList,...res.data]
					}
				})
			}
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
		.active {
			color:  #1296db;
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
	.no-data {
		margin-top: 40rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		image {
			width: 350rpx;
			height: 300rpx;
		}
	}
	.loading {
		text-align: center;
		font-size: 26rpx;
		color: #888;
		view {
			line-height: 2rem;
		}
	}
</style>
