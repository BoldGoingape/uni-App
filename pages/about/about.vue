<template>
	<view>
		<h1>我是about</h1>
		<navigator url="/pages/index/index" open-type="reLaunch">跳转首页</navigator>
		<image class="log" src="../../static/logo.png" @click="clickImg"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			clickImg(){
				uni.showToast({
					title: '点击',
					duration: 2000,
					icon:"error",
					mask:true
				});
			}
		}
	}
</script>

<style lang="scss">

</style>
