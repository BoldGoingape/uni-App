<template>
	<view class="nav">
	<view class="item " :class="isActive==index ? 'active' : ''" v-for="(item,index) in newArr" :key="item.id" @click="clickNave(index)">{{item.title}}</view>
		<view class="content">
			<view class="texturl" v-for="item in pocurl" :key="item.id">
				<img :src="item.url" alt="" srcset="">
			</view>
		</view>
	
	</view>

</template>

<script>
	export default {
		data() {
			return {
				newArr:[
					{id:1,title:'首页'},
					{id:2,title:'文件'},
					{id:3,title:'编辑'},
					{id:4,title:'查找'}
				],
				isActive:0,
				value:'test',
				pocurl:[]
			};
		},
		methods:{
			clickNave(index){
				this.isActive=index
			},
			getImg(){
					uni.showLoading({
						title:"数据加载中.."
					}),
					uni.request({
						url:"https://api.thecatapi.com/v1/images/search",
						data:{
							limit:30
						},
						success:res=>{
							this.pocurl=res.data,
							console.log(res.data);
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
		onLoad() {
			this.getImg()
		}
	}
</script>

<style lang="scss">
	.nav{
		display: flex;
		justify-content: space-around;
		align-items: center;
		.item{
			flex: 1;
			line-height: 90rpx;
			background:#ccc;
			text-align: center;
			&.active{
				background-color: greenyellow;
				color: #ccc;
			}
		}
		.item.active{
			
		}
	}
	.content {
	position: absolute;
	top:100rpx
	}
		img{
			width: 100%;
			height: 150rpm;
		}
</style>
