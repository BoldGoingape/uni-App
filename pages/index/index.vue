<template>
	<view class="content">
		<view class="text-area">
		</view>
		<view class="item" v-for="(value,index) in iconType" :key="index">
		    <icon :type="value" size="26"/>
		    <text>{{value}}</text>
		</view>
		<text selectable >{{text}}</text>
		<text space="ensp">哈哈啊     &gt;       哈哈</text>
		<view class="">
			{{text}}
		</view>
		<scroll-view class="scroll" selectable  show-scrollbar=true scroll-x scroll-y>
			<view class="group">
				<view class="item">
					111
				</view>
				<view class="item">
					222
				</view>
				<view class="item">
					333
				</view>
				<view class="item">
					444
				</view>
				<view class="item">
					555
				</view>
				<view class="item">
					666
				</view>
			</view>
		</scroll-view>
		//轮播
		<view class="uni-margin-wrap">
					<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
						:duration="duration" indicator-color="red" indicator-active-color="green" >
						<swiper-item v-for="item in pocurl" :key="item.id">
							<view class="swiper-item uni-bg-red">
								<img :src="item.url" alt="" srcset="">
							</view>
						</swiper-item>
					</swiper>
				</view>
				<view class="swiper-list">
							<view class="uni-list-cell uni-list-cell-pd">
								<view class="uni-list-cell-db">指示点</view>
								<switch :checked="indicatorDots" @change="changeIndicatorDots" />
							</view>
							<view class="uni-list-cell uni-list-cell-pd">
								<view class="uni-list-cell-db">自动播放</view>
								<switch :checked="autoplay" @change="changeAutoplay" />
							</view>
						</view>
						
						<!--  redirect-->
						<navigator url="/pages/list/list" open-type="navigate">跳转列表</navigator>
					
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				  iconType: ['success'],
				  text:"新年快乐！",
				   indicatorDots: true,
				    autoplay: true,
				    interval: 2000,
				    duration: 500,
					pocurl:[]
			}
		},
		onLoad() {
			uni.showLoading({
				title:"数据加载中。。。"
			})
			uni.setTabBarBadge({
			  index: 3,
			  text: '3'
			}),
			uni.showTabBarRedDot({
				index:1,
			})
			setTimeout(()=>{
				uni.removeTabBarBadge({
					index:3,
					text:"3"
				}),
				uni.hideTabBarRedDot({
					index:1
				}),
				uni.hideLoading()
			},5000)
		},
		methods: {
		changeIndicatorDots(e) {
            this.indicatorDots = !this.indicatorDots
        },
        changeAutoplay(e) {
            this.autoplay = !this.autoplay
        },
        intervalChange(e) {
            this.interval = e.target.value
        },
        durationChange(e) {
            this.duration = e.target.value
        },
		getImg(){
				uni.showLoading({
					title:"数据加载中.."
				}),
				uni.request({
					url:"https://api.thecatapi.com/v1/images/search?limit=1.5",
					success:res=>{
						this.pocurl=res.data,
						setTimeout(()=>{
							uni.hideLoading()
						},650)
					},
					fail: (err) => {
						console.log(err)
					},
					complete: () => {
						uni.hideLoading()
					}
				})
			}
		},
		mounted() {
			this.getImg()
			},
		
	}
</script>

<style lang="scss">
		.uni-margin-wrap {
			width: 690rpx;
			width: 100%;
			img{
				width: 100%;
				height: 100%;
			}
		}
		.swiper {
			height: 300rpx;
		}
		.swiper-item {
			display: block;
			height: 300rpx;
			line-height: 300rpx;
		}
		.swiper-list {
			margin-top: 40rpx;
			margin-bottom: 0;
		}
		.uni-common-mt {
			margin-top: 60rpx;
			position: relative;
		}
		.info {
			position: absolute;
			right: 20rpx;
		}
		.uni-padding-wrap {
			width: 550rpx;
			padding: 0 100rpx;
		}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.text-area{
			width: 750rpx;
			height: 250rpx;
			background-color: red;
		}
	}
	.scroll{
	border: 1px solid red;
	//改成内边框
	box-sizing: border-box;
	height: 220rpx;
	.group{
		white-space:nowrap;
		.item{
			width: 220rpx;
			height: 220rpx;
			background-color: aqua;
			display: inline-block;
			margin-right: 10rpm;
		}
	}
	}
	
</style>
