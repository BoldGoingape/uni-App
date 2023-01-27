<template>
	<view class="nav">
		<view class="item " :class="isActive==index ? 'active' : ''" v-for="(item,index) in newArr" :key="item.id" @click="clickNave(index)">{{item.title}}</view>
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
				isActive:0
			};
		},
		methods:{
			clickNave(index){
				this.isActive=index
			}
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
		
</style>
