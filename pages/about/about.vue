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
				itemLists:['A', 'B', 'C', 'D']
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
				//交互
				let that =this
				uni.showActionSheet({
					itemList: this.itemLists,
					success: function (res) {
						console.log('选中了第' + (res.tapIndex + 1) + '个按钮');
						console.log(res);
						console.log(that.itemLists[res.tapIndex]);
					},
					fail: function (res) {
						console.log(res.errMsg);
					}
				});
			//模态弹窗
			// uni.showModal({
			// 	title: '提示',
			// 	content: '这是一个模态弹窗',
			// 	success: function (res) {
			// 		console.log(res);
			// 		if (res.confirm) {
			// 			console.log('用户点击确定');
			// 			uni.navigateTo({
			// 				url:"/pages/index/index",
			// 			})
			// 		} else if (res.cancel) {
			// 			console.log('用户点击取消');
			// 		}
			// 	}
			// });
			//showMOdal
					// uni.showModal({
					// 	title:"电话号",
					// 	placeholderText:"请输入手机号",
					// 	showCancel:false,
					// 	editable:true,
					// 	success(res) {
					// 		console.log(res.content);
					// 	}
					// })
			}
		}
	}
</script>

<style lang="scss">

</style>
