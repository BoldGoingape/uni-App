<template>
	<view>
		<navigator url="/pages/index/index" open-type="reLaunch">跳转首页</navigator>
		<img :src="imgsrc" alt="" srcset="" @click=getImg(imgsrc)>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgsrc:""
			};
		},
		methods:{
			getImg(ing){
				uni.showLoading({
					title:"数据加载中.."
				})
				uni.request({
					url:"https://dog.ceo/api/breeds/image/random",
					success:res=>{
						this.imgsrc=res.data.message,
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
		watch:{
			imgsrc:{
				handler(newValue,oldValue){
					
					console.log("值改变了",newValue)
				}
			}
		},
		mounted(){
			
		},
		onLoad() {
			uni.setNavigationBarTitle ({
				title:"js操作origin"
			}),
			uni.showNavigationBarLoading();
			setTimeout(()=>{
				uni.hideNavigationBarLoading()
			},1500),
			this.getImg();
		}
	}
</script>

<style lang="scss">
	img{
		width: 100%;
		height: 150rpm;
	}
</style>
