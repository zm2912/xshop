<template>
	<view class="container">
		<!-- 小程序头部兼容 -->
		<!-- 头部轮播 -->
		<view class="carousel-section">
			<!-- 标题栏和状态栏占位符 -->
			<!-- 背景色区域 -->
			<view class="titleNview-background" :style="{backgroundColor:'#FFE437'}"></view>
			<swiper class="carousel" circular @change="swiperChange" :autoplay="true">
				<swiper-item v-for="(item, index) in carouselList" :key="index" class="carousel-item" @click="navToLink(item)">
					<image :src="item.image" />
				</swiper-item>
			</swiper>
			<!-- 自定义swiper指示器 -->
		</view>
		<!-- 分类 -->	
		<view class="cate-section">
			<view class="cate-item" v-for="(item, index) in navListone" :key="index" @click="navToLink(item)">
				<image :src="item.image"></image>
				<text>{{item.title}}</text>
			</view>
		</view>
		<view class="cate-section">
			<view class="cate-item" v-for="(itemt, index) in navListtow" :key="index" @click="navToLink(itemt)">
				<image :src="itemt.image"></image>
				<text>{{itemt.title}}</text>
			</view>
		</view>
		<!-- 通告 -->
		<view style="text-align: center;">
			<image src="../../static/image@2x.png" style="width:100%;height:120px;"></image>
		</view>
		<!-- 团购楼层 -->
		<view>
			<view class="f-header m-t" @click="goGroupCategory">
				<image src="/static/time@2x.png"></image>
				<view class="tit-box">
					<text class="tit">限时秒杀</text>
				</view>
				<text style="color: #999999;">更多</text>
				<image src="../../static/xiayibu.png" style="width:20px;height:20px;margin-left: 5px;"></image>
			</view>
			
			<view class="guess-section">
				<view v-for="(item, index) in data.home_groupon_products" :key="index" class="guess-item" @click="navToDetailPage(item)">
					<view class="image-wrapper">
						<image :src="item.image[0]" mode="aspectFill"></image>
					</view>
					<view class="title demo">{{item.title}}</view>
					<view class="progress-view">
						<text class="porgress-text">已抢40%</text>
						<progress percent="40" stroke-width="20"  border-radius="10" activeColor="#FFE437"  backgroundColor="rgba(255,228,55,0.4)"/>
					</view>
					<view class="title-price">
						<text class="price">￥{{item.price}}</text>
						<text class="under-price">￥{{item.skus[0].price}}</text>
					</view>
					<view class="title-price-button">
						<text style="height: 52px;">马上抢购</text>
					</view>
				</view>
			</view>
		</view>
		<!-- 团购楼层 -->
		<view>
			<view class="f-header m-t" @click="goGroupCategory">
				<image src="/static/tuan@2x.png"></image>
				<view class="tit-box">
					<text class="tit">拼团抢购</text>
				</view>
				<text style="color: #999999;">更多</text>
				<image src="../../static/xiayibu.png" style="width:20px;height:20px;margin-left: 5px;"></image>
			</view>
			
			<view class=".guess-section-goodsSwiper">
				<swiper class="carousel-swiper-center" @change="swiperChange">
					<swiper-item v-for="(item, index) in carouselList" :key="index" class="carousel-item-center" @click="navToLink(item)">
						<image :src="item.image"/>
						<view class="title">AnnoMundi 宫廷泡泡袖短袖针织上衣女夏设计感小众撞色拼接T恤</view>
						<text class="price">￥44.65</text>
						<view class="number">已拼2332件</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		<view>
			<view class="f-header m-t" @click="goGroupCategory">
				<view class="tit-box">
					<text class="tit">好物严选</text>
				</view>
				<text style="color: #999999;">更多</text>
				<image src="../../static/xiayibu.png" style="width:20px;height:20px;margin-left: 5px;"></image>
			</view>
			<view class="guess-section-goods-view">
				<view class="guess-section-goods" v-for="(row, index) in data.home_recommend_products" :key="index">
					<scroll-view>
						<view>
							<view v-for="(item, i) in row.products" :key="i" @click="navToDetailPage(item)">
								<image :src="item.image[0]" mode="aspectFill" class="image"></image>
								<view class="title demo">{{item.title}}</view>
								<text class="price">￥{{item.price}}</text>
								<text class="under-price">￥{{item.skus[0].price}}</text>
							</view>
							<view @click="navToLink(row)">
							</view>
						</view>
					</scroll-view>
				</view>
				<view class="guess-section-goods" v-for="(row, index) in data.home_recommend_products" :key="index">
					<scroll-view>
						<view>
							<view v-for="(item, i) in row.products" :key="i" @click="navToDetailPage(item)">
								<image :src="item.image[0]" mode="aspectFill" class="image"></image>
								<view class="title demo">{{item.title}}</view>
								<text class="price">￥{{item.price}}</text>
								<text class="under-price">￥{{item.skus[0].price}}</text>
							</view>
							<view @click="navToLink(row)">
							</view>
						</view>
					</scroll-view>
				</view>
				<view class="guess-section-goods" v-for="(row, index) in data.home_recommend_products" :key="index">
					<scroll-view>
						<view>
							<view v-for="(item, i) in row.products" :key="i" @click="navToDetailPage(item)">
								<image :src="item.image[0]" mode="aspectFill" class="image"></image>
								<view class="title demo">{{item.title}}</view>
								<text class="price">￥{{item.price}}</text>
								<text class="under-price">￥{{item.skus[0].price}}</text>
							</view>
							<view @click="navToLink(row)">
							</view>
						</view>
					</scroll-view>
				</view>
				<view class="guess-section-goods" v-for="(row, index) in data.home_recommend_products" :key="index">
					<scroll-view>
						<view>
							<view v-for="(item, i) in row.products" :key="i" @click="navToDetailPage(item)">
								<image :src="item.image[0]" mode="aspectFill" class="image"></image>
								<view class="title demo">{{item.title}}</view>
								<text class="price">￥{{item.price}}</text>
								<text class="under-price">￥{{item.skus[0].price}}</text>
							</view>
							<view @click="navToLink(row)">
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</view>
		<view>
			<view class="f-header m-t" @click="goGroupCategory">
				<view class="tit-box">
					<text class="tit">福利推送</text>
				</view>
				<text style="color: #999999;">更多</text>
				<image src="../../static/xiayibu.png" style="width:20px;height:20px;margin-left: 5px;"></image>
			</view>
			<view class="guess-section-push" v-for="(item, index) in guessList.list" :key="index">
				<image :src="item.url" style="width: 100%;height: 130px;"></image>
				<view class="number">已售{{item.number}}件</view>
				<view class="title">{{item.title}}</view>
				<view class="title-price">
					<text class="price">￥{{item.price}}</text>
				</view>
				<view class="title-price-button">
					<text style="height: 52px;">立即购买</text>
				</view>
			</view>
		</view>

		


	</view>
</template>

<script>
	import {
		mapActions,
		mapState
	} from 'vuex'
	import grouponBox from './child/grouponBox';
	import notice from './child/notice';
	import goodsSwiper from "@/components/pyh-goodsSwiper/pyh-goodsSwiper.vue"
	export default {
		components: {
			grouponBox,
			notice,
			goodsSwiper
		},
		data() {
			return {
				titleNViewBackground: '',
				swiperCurrent: 0,
				carouselList: [],
				navList: [],
				navListone: [],
				navListtow: [],
				goodsList: [],
				adList: [],
				noticeList: [],
				data: {},
				guessList:{
					list:[{
						url: '../../static/imagetop@2x.png',
						number: "2048",
						title: "低热量高饱腹感奇亚籽及时燕麦片",
						price:"44.65"
					},{
						url: '../../static/imagetop@2x.png',
						number: "2048",
						title: "低热量高饱腹感奇亚籽及时燕麦片",
						price:"44.65"
					}
					]
				},
				detail:{
					list:[
						{
							id:1,
							img:"https://shops.balala.fun/uploads/20200428/e135e6c61919780e43bf208aa2a63e0f.png",
							name:"名称",
							price:"0.00",
							number:"20"
						},
						{
							id:2,
							img:"https://shops.balala.fun/uploads/20200428/e135e6c61919780e43bf208aa2a63e0f.png",
							name:"名称",
							price:"0.00",
							number:"20"
						},
						{
							id:3,
							img:"https://shops.balala.fun/uploads/20200428/e135e6c61919780e43bf208aa2a63e0f.png",
							name:"名称",
							price:"0.00",
							number:"20"
						},
						{
							id:4,
							img:"https://shops.balala.fun/uploads/20200428/e135e6c61919780e43bf208aa2a63e0f.png",
							name:"名称",
							price:"0.00",
							number:"20"
						}
					]
				},
				config:{
					more:true,
					autoplay:false,
					multiple:2,
					shadow:true
				}
			};
		},

		onLoad() {
			this.init()
		},
		computed: {
		},
		methods: {
			...mapActions(['SAVE_HOME_PRODUCTS']),
			getHomeProducts() {
				this.$http.get('home.products').then(res => {
					this.data = res.data
				}).catch(e => {
				})
			},
			init() {
				return Promise.all([this.getHomeProducts(), this.getNavData()])
			},
			getNavData() {
				this.$http.post('nav', {
					nav_type: [0, 1, 2, 4]
				}).then(res => {
					this.carouselList = res.data[0] || [];
					// this.navList = res.data[1] || [];
					if (res.data[1].length > 5) {
						for (let nav=0; nav<res.data[1].length; nav++){
							if (nav<5) {
								console.log('5个')
								this.navListone = res.data[1].slice(0, 5)
								console.log(this.navListone, 'this.navListone')
							} else {
								console.log('超过5个')
								this.navListtow = res.data[1].slice(5,)
								console.log(this.navListtow, "this.navListtow")
							}
						}
					} else {
						console.log('刚好5个')
						this.navListone = res.data[1] || [];
					}
					this.adList = res.data[2] || [];
					this.noticeList = res.data[4] || [];
					this.titleNViewBackground = this.carouselList[0] ? (this.carouselList[0].params ? (this.carouselList[0].params['color'] || '') : '') : ''
				})
			},
			goCategory() {
				uni.switchTab({
					url: '/pages/category/category'
				})
			},
			goGroupCategory(item) {
				uni.navigateTo({
					url: '/pages/product/list?groupon=1'
				})
			},
			//轮播图切换修改背景色
			swiperChange(e) {
				const index = e.detail.current;
				this.swiperCurrent = index;
				this.titleNViewBackground = this.carouselList[index].params ? (this.carouselList[index].params.color|| '') : ''
			},
			navToDetailPage(item) {
				uni.navigateTo({
					url: '/pages/product/product?id=' + item.id
				})
			},
			navToLink(item) {
				this.$meRouter(item)
			},
			submit(e) {
				this.goSearch(e.detail.value)
			},
			goSearch(kw) {
				uni.navigateTo({
					url: '/pages/product/list?kw=' + kw
				})
			}
		},
		

		
		// #ifndef MP
		// 标题栏input搜索框点击
		/* onNavigationBarSearchInputClicked: function(e) {
			console.log(e)
		}, */
		onNavigationBarSearchInputConfirmed: function(e) {
			this.goSearch(e.text)
		},
		//点击导航栏 buttons 时触发
		onNavigationBarButtonTap(e) {
			const index = e.index;
			if (index === 0) {
				/// this.$api.msg('点击了扫描');
			} else if (index === 1) {
				return false
				// #ifdef APP-PLUS
				const pages = getCurrentPages();
				const page = pages[pages.length - 1];
				const currentWebview = page.$getAppWebview();
				currentWebview.hideTitleNViewButtonRedDot({
					index
				});
				// #endif
				uni.navigateTo({
					url: '/pages/notice/notice'
				})
			}
		},
		// #endif
		
		onPullDownRefresh() {
			this.init().then(e => {
				uni.stopPullDownRefresh()
			}).catch(e => {
				uni.stopPullDownRefresh()
			})
		}
	}
</script>

<style lang="scss">
	/* #ifdef MP */
	.mp-search-box {
		position: absolute;
		left: 0;
		top: 30upx;
		z-index: 9999;
		width: 100%;
		padding: 0 80upx;

		.ser-input {
			flex: 1;
			height: 56upx;
			line-height: 56upx;
			text-align: center;
			font-size: 28upx;
			color: $font-color-base;
			border-radius: 20px;
			background: rgba(255, 255, 255, .6);
		}
	}

	page {
		.cate-section {
			position: relative;
			z-index: 5;
			margin-top: -20upx;
		}

		.carousel-section {
			padding: 0;

			.titleNview-placing {
				padding-top: 0;
				height: 0;
			}

			.carousel {
				.carousel-item {
					padding: 0;
				}
			}

			.swiper-dots {
				left: 45upx;
				bottom: 40upx;
			}
		}
	}

	/* #endif */
.porgress-text{
	position: absolute;
	font-size:12px;
	font-family:PingFangSC-Medium,PingFang SC;
	font-weight:500;
	color:rgba(0,0,0,1);
}
.progress-view{
	position: relative;
	text-align: center;
	top: -35%;
	width: 65%;
	left: 35%;
}
.demo {
		display: -webkit-box;
		overflow: hidden;
		text-overflow: ellipsis;
		word-wrap: break-word;
		white-space: normal !important;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
	}
	page {
		background: #fff;
	}


	/* 头部 轮播图 */
	.carousel-section {
		position: relative;
		padding-top: 10px;

		.titleNview-placing {
			height: var(--status-bar-height);
			padding-top: 44px;
			box-sizing: content-box;
		}

		.titleNview-background {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 270upx;
			transition: .4s;
			border-bottom-right-radius: 20%;
			border-bottom-left-radius: 20%;
		}
	}

	.carousel {
		width: 100%;
		height: 350upx;

		.carousel-item {
			width: 100%;
			height: 100%;
			padding: 0 28upx;
			overflow: hidden;
			text-align: center;
		}

		image {
			width: 90%;
			height: 90%;
			border-radius: 10upx;
		}
	}
	.carousel-swiper-center{
		width: 100%;
		height: 350upx;
		.carousel-item-center {
			padding: 28upx 0 0 10upx;
			overflow: hidden;
			.title{
				font-family:PingFangSC-Medium,PingFang SC;
				font-weight:500;
				color:rgba(51,51,51,1);
				line-height:20px;
				display: -webkit-box;
				overflow: hidden;
				text-overflow: ellipsis;
				word-wrap: break-word;
				white-space: normal !important;
				-webkit-line-clamp: 1;
				-webkit-box-orient: vertical;
				width: 120px;
			}
			.price {
				font-size: $font-lg;
				color: $uni-color-primary;
				line-height: 1;
			}
			.number{
				font-family:PingFangSC-Regular,PingFang SC;
				font-weight:400;
				color:rgba(153,153,153,1);
			}
			image {
			width: 120px;
			height: 100px;
			display: inline-block;
			overflow: hidden;
			
			}
		}
	}

	.swiper-dots {
		display: flex;
		position: absolute;
		left: 60upx;
		bottom: 15upx;
		width: 72upx;
		height: 36upx;
		background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAABkCAYAAADDhn8LAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTMyIDc5LjE1OTI4NCwgMjAxNi8wNC8xOS0xMzoxMzo0MCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0UmVmPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VSZWYjIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6OTk4MzlBNjE0NjU1MTFFOUExNjRFQ0I3RTQ0NEExQjMiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6OTk4MzlBNjA0NjU1MTFFOUExNjRFQ0I3RTQ0NEExQjMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTcgKFdpbmRvd3MpIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6Q0E3RUNERkE0NjExMTFFOTg5NzI4MTM2Rjg0OUQwOEUiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6Q0E3RUNERkI0NjExMTFFOTg5NzI4MTM2Rjg0OUQwOEUiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz4Gh5BPAAACTUlEQVR42uzcQW7jQAwFUdN306l1uWwNww5kqdsmm6/2MwtVCp8CosQtP9vg/2+/gY+DRAMBgqnjIp2PaCxCLLldpPARRIiFj1yBbMV+cHZh9PURRLQNhY8kgWyL/WDtwujjI8hoE8rKLqb5CDJaRMJHokC6yKgSCR9JAukmokIknCQJpLOIrJFwMsBJELFcKHwM9BFkLBMKFxNcBCHlQ+FhoocgpVwwnv0Xn30QBJGMC0QcaBVJiAMiec/dcwKuL4j1QMsVCXFAJE4s4NQA3K/8Y6DzO4g40P7UcmIBJxbEesCKWBDg8wWxHrAiFgT4fEGsB/CwIhYE+AeBAAdPLOcV8HRmWRDAiQVcO7GcV8CLM8uCAE4sQCDAlHcQ7x+ABQEEAggEEAggEEAggEAAgQACASAQQCCAQACBAAIBBAIIBBAIIBBAIABe4e9iAe/xd7EAJxYgEGDeO4j3EODp/cOCAE4sYMyJ5cwCHs4rCwI4sYBxJ5YzC84rCwKcXxArAuthQYDzC2JF0H49LAhwYUGsCFqvx5EF2T07dMaJBetx4cRyaqFtHJ8EIhK0i8OJBQxcECuCVutxJhCRoE0cZwMRyRcFefa/ffZBVPogePihhyCnbBhcfMFFEFM+DD4m+ghSlgmDkwlOgpAl4+BkkJMgZdk4+EgaSCcpVX7bmY9kgXQQU+1TgE0c+QJZUUz1b2T4SBbIKmJW+3iMj2SBVBWz+leVfCQLpIqYbp8b85EskIxyfIOfK5Sf+wiCRJEsllQ+oqEkQfBxmD8BBgA5hVjXyrBNUQAAAABJRU5ErkJggg==);
		background-size: 100% 100%;

		.num {
			width: 36upx;
			height: 36upx;
			border-radius: 50px;
			font-size: 24upx;
			color: #fff;
			text-align: center;
			line-height: 36upx;
		}

		.sign {
			position: absolute;
			top: 0;
			left: 50%;
			line-height: 36upx;
			font-size: 12upx;
			color: #fff;
			transform: translateX(-50%);
		}
	}

	/* 分类 */
	.cate-section {
		display: flex;
		justify-content: space-around;
		align-items: center;
		flex-wrap: wrap;
		padding: 30upx 22upx;
		background: #fff;
		margin-bottom: 16upx;

		.cate-item {
			display: flex;
			flex-direction: column;
			align-items: center;
			font-size: $font-sm + 2upx;
			color: $font-color-dark;
		}

		/* 原图标颜色太深,不想改图了,所以加了透明度 */
		image {
			width: 88upx;
			height: 88upx;
			margin-bottom: 14upx;
			border-radius: 50%;
			// opacity: .7;
			// box-shadow: 4upx 4upx 20upx rgba(250, 67, 106, 0.3);
		}
	}

	.ad-1 {
		width: 100%;
		height: 210upx;
		padding: 10upx 0;
		background: #fff;

		image {
			width: 100%;
			height: 100%;
		}
	}

	/* 秒杀专区 */
	.seckill-section {
		padding: 4upx 30upx 24upx;
		background: #fff;

		.s-header {
			display: flex;
			align-items: center;
			height: 92upx;
			line-height: 1;

			.s-img {
				width: 140upx;
				height: 30upx;
			}

			.tip {
				font-size: $font-base;
				color: $font-color-light;
				margin: 0 20upx 0 40upx;
			}

			.timer {
				display: inline-block;
				width: 40upx;
				height: 36upx;
				text-align: center;
				line-height: 36upx;
				margin-right: 14upx;
				font-size: $font-sm+2upx;
				color: #fff;
				border-radius: 2px;
				background: rgba(0, 0, 0, .8);
			}

			.icon-you {
				font-size: $font-lg;
				color: $font-color-light;
				flex: 1;
				text-align: right;
			}
		}

		.floor-list {
			white-space: nowrap;
		}

		.scoll-wrapper {
			display: flex;
			align-items: flex-start;
		}

		.floor-item {
			width: 150upx;
			margin-right: 20upx;
			font-size: $font-sm+2upx;
			color: $font-color-dark;
			line-height: 1.8;

			image {
				width: 150upx;
				height: 150upx;
				border-radius: 6upx;
			}

			.price {
				color: $uni-color-primary;
			}
			
		}
	}

	.f-header {
		display: flex;
		align-items: center;
		height: 100upx;
		padding: 6upx 30upx 8upx;
		background: #fff;
		margin-top: 20px;
		image {
			flex-shrink: 0;
			width: 40upx;
			height: 40upx;
		}

		.tit-box {
			flex: 1;
			display: flex;
			flex-direction: column;
		}

		.tit {
			font-size: $font-lg +2upx;
			color: #font-color-dark;
			line-height: 1.3;
			font-weight:500;
		}

		.tit2 {
			font-size: $font-sm;
			color: $font-color-light;
		}

		.icon-you {
			font-size: $font-lg +2upx;
			color: $font-color-light;
		}
	}

	/* 团购楼层 */
	.group-section {
		background: #fff;

		.g-swiper {
			height: 650upx;
			padding-bottom: 30upx;
		}

		.g-swiper-item {
			width: 100%;
			padding: 0 30upx;
			display: flex;
		}

		image {
			width: 100%;
			height: 460upx;
			border-radius: 4px;
		}

		.g-item {
			display: flex;
			flex-direction: column;
			overflow: hidden;
		}

		.left {
			flex: 1.2;
			margin-right: 24upx;

			.t-box {
				padding-top: 20upx;
			}
		}

		.right {
			flex: 0.8;
			flex-direction: column-reverse;

			.t-box {
				padding-bottom: 20upx;
			}
		}

		.t-box {
			height: 160upx;
			font-size: $font-base+2upx;
			color: $font-color-dark;
			line-height: 1.6;
		}

		.price {
			color: $uni-color-primary;
		}

		.m-price {
			font-size: $font-sm+2upx;
			text-decoration: line-through;
			color: $font-color-light;
			margin-left: 8upx;
		}

		.pro-box {
			display: flex;
			align-items: center;
			margin-top: 10upx;
			font-size: $font-sm;
			color: $font-base;
			padding-right: 10upx;
		}

		.progress-box {
			flex: 1;
			border-radius: 10px;
			overflow: hidden;
			margin-right: 8upx;
		}
	}

	/* 分类推荐楼层 */
	.hot-floor {
		width: 100%;
		overflow: hidden;
		margin: 20upx 0;
		.cat_name {
			background: #fff;
			margin-left: 5px;
			padding: 20upx 0 20upx 20upx;
			border-left: 3px solid #FC7592;
			font-size: $font-base + 4upx;
		}
		.floor-img-box {
			width: 100%;
			height: 320upx;
			position: relative;

			&:after {
				content: '';
				position: absolute;
				left: 0;
				top: 0;
				width: 100%;
				height: 100%;
				background: linear-gradient(rgba(255, 255, 255, .06) 30%, #f8f8f8);
			}
		}

		.floor-img {
			width: 100%;
			height: 100%;
		}

		.floor-list {
			white-space: nowrap;
			padding: 20upx;
			padding-right: 50upx;
			border-radius: 6upx;
			margin-left: 10upx;
			background: #fff;
			box-shadow: 1px 1px 5px rgba(0, 0, 0, .2);
			position: relative;
			z-index: 1;
		}

		.scoll-wrapper {
			display: flex;
			align-items: flex-start;
		}

		.floor-item {
			width: 180upx;
			margin-right: 20upx;
			font-size: $font-sm+2upx;
			color: $font-color-dark;
			line-height: 1.8;

			image {
				width: 180upx;
				height: 180upx;
				border-radius: 6upx;
			}

			.price {
				color: $uni-color-primary;
			}
		}

		.more {
			display: flex;
			align-items: center;
			justify-content: center;
			flex-direction: column;
			flex-shrink: 0;
			width: 180upx;
			height: 180upx;
			border-radius: 6upx;
			background: #f3f3f3;
			font-size: $font-base;
			color: $font-color-light;

			text:first-child {
				margin-bottom: 4upx;
			}
		}
	}

.guess-section-goodsSwiper{
	display: flex;
	flex-wrap: wrap;
	background: #fff;
	width: 95%;
	margin: auto;
	box-shadow:0px 2px 10px 0px rgba(238,238,238,1);
}
.guess-section-push{
	display: flex;
	flex-wrap: wrap;
	padding: 30upx 30upx;
	background: #fff;
	width: 95%;
	margin: auto;
	box-shadow:0px 2px 10px 0px rgba(238,238,238,1);
	margin-bottom: 5px;
	.number{
		position: absolute;
		color: #FFFFFF;
		font-family:PingFangSC-Medium,PingFang SC;
		font-weight:500;
		color:rgba(255,255,255,1);
		padding:0 5px;
		border-radius:16px;
		font-size: 14px;
		margin-top: 2%;
		left: 8%;
		border:1px solid rgba(255,255,255,1);
	}
	.title{
		margin-top: 5%;
		margin-bottom: 12%;
	}
	.title-price{
		font-size: $font-lg;
		color: $font-color-dark;
		position: absolute;
		width: 100%;
		margin-top: 47%;
	}
	.price{
		font-size: $font-lg;
		color: $uni-color-primary;
		line-height: 1;
	}
	.title-price-button{
		font-size: $font-lg;
		color: $font-color-dark;
		position: absolute;
		width: 20%;
		left: 70%;
		background:rgba(250,72,0,1);
		border-radius:25px;
		text-align: center;
		margin-top: 45%;
		font-family:PingFangSC-Medium,PingFang SC;
		font-weight:500;
		color:rgba(255,255,255,1);
		line-height:33px;
	}
}
	/* 猜你喜欢 */
	.guess-section {
		display: flex;
		flex-wrap: wrap;
		padding: 0 30upx;
		background: #fff;
		width: 95%;
		margin: auto;
		box-shadow:0px 2px 10px 0px rgba(238,238,238,1);

		.guess-item {
			display: flex;
			flex-direction: column;
			width: 100%;
			padding-bottom: 40upx;

			&:nth-child(2n+1) {
				margin-right: 4%;
			}
		}

		.image-wrapper {
			width: 35%;
			height: 200rpx;
			border-radius: 3px;
			overflow: hidden;
			display: inline-block;

			image {
				width: 100%;
				height: 200rpx;
				opacity: 1;
			}
		}

		.title {
			font-size: $font-lg;
			color: $font-color-dark;
			position: absolute;
			width: 60%;
			left: 36%;
			margin-top: 3%;
		}
		.title-price{
			font-size: $font-lg;
			color: $font-color-dark;
			position: absolute;
			width: 60%;
			left: 36%;
			margin-top: 25%;
		}
		.title-price-button{
			font-size: $font-lg;
			color: $font-color-dark;
			position: absolute;
			width: 20%;
			left: 70%;
			background:rgba(250,72,0,1);
			border-radius:25px;
			text-align: center;
			margin-top: 23%;
			font-family:PingFangSC-Medium,PingFang SC;
			font-weight:500;
			color:rgba(255,255,255,1);
			line-height:33px;
		}

		.price {
			font-size: $font-lg;
			color: $uni-color-primary;
			line-height: 1;
		}
		
		.under-price {
			font-size: $font-base;
			color: gray;
			text-decoration: line-through;
		}
	}
	/* 好物严选 */
	.guess-section-goods-view{
		justify-content: space-between;
		text-align: center;
		.guess-section-goods {
			display: inline-block;
			flex-wrap: wrap;
			padding: 30upx 30upx;
			background: #fff;
			width: 46%;
			box-shadow:0px 2px 10px 0px rgba(238,238,238,1);
			border-radius:10px;
			margin-bottom: 5px;
			text-align: left;
			.image{
				width: 160px!important;
				height: 120px;
			}
			.price {
				font-size: $font-lg;
				color: $uni-color-primary;
				line-height: 1;
			}
			
			.under-price {
				font-size: $font-base;
				color: gray;
				text-decoration: line-through;
			}
		}
	}
	.coupon-box {
		padding: 20upx;
		background: #fff;
		margin: 20upx 0;
		display: flex;
		
		.coupon-item {
			width: 70vw;
			display: flex;
			font-size: $font-base;
			background: #F85169;
			color: #fff;
			border-radius: 10upx;
			.left {
				flex: 2;
				display: flex;
				flex-direction: column;
				padding: 20upx;
			}
			.line {
				width: 26upx;
				border: 1px solid #fff;
				display: flex;
				justify-content: space-between;
				position: relative;
				.circle {
					    width: 22upx;
						height: 22upx;
						border-radius: 50%;
						background: #fff;
						position: absolute;
					&.l {
						
						top: -18upx;
					}
					&.r {
						bottom: -18upx;
					}
				}
			}
			.right {
				flex: 1;
				display: flex;
				flex-direction: column;
				padding: 20upx;
				justify-content: center;
				align-items: center;
			}
			.txt {
				&.big-txt {
					font-size: $font-base + 6upx;
					margin: 10upx 0;
				}
			}
		}
	}

	
</style>
