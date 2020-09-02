<template>
	<view class="content">
		<image src="../../static/img/logo.png" mode="widthFix" class="logo"></image>
		<image src="../../static/img/a1.png" mode="widthFix" class="info"></image>
		<image src="../../static/img/a2.png" mode="widthFix" class="txt"></image>
		<view class="shuru">
			<view class="shuru_box">
				<view class="biaoti">姓名</view>
				<input type="text" value="" placeholder="" placeholder-class="kk" v-model="yiyuan" class="shurutiao"/>
			</view>
			<view class="shuru_box">
				<view class="biaoti">医院</view>
				<input type="text" value="" placeholder="" v-model="xingming" class="shurutiao"/>
			</view>
		</view>
		
		<view class="btn" @click="tijiao"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				yiyuan:'',
				xingming:''
			}
		},
		onLoad() {

		},
		methods: {
			tijiao(){
				if (this.yiyuan && this.xingming) {
					console.log(this.yiyuan)
					console.log(this.xingming)
					uni.request({
						url:'http://3w.donglianguoji.com/app/chuanshipin/php/txt.php',
						method:'POST',
						header:{'content-type': 'application/x-www-form-urlencoded'},
						data:{yiyuan:this.yiyuan,xingming:this.xingming},
						success: (e) => {
							console.log(e.data)
							let id = e.data
							uni.setStorageSync('shipinid',id)
							uni.redirectTo({
								url:'../shouquan/shouquan'
							})
						}
						
					})
				} else{
					uni.showModal({
						title:'提示',
						content:'请输入医院名称和姓名',
						showCancel:false
					})
				}
			}
		}
	}
</script>

<style>
	.content {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		background: url(../../static/img/BG1.jpg) no-repeat center bottom;
		background-size: 100% auto;
		padding-top: 47rpx;
	}
	
	.logo{width: 666rpx;height: 98rpx;margin-bottom: 12rpx;}
	.info{width: 558rpx;height: 44rpx;margin-bottom: 43rpx;}
	.txt{width: 294rpx;height: 56rpx;margin-bottom: 66rpx;}
	
	.shuru{width: 502rpx;height: 222rpx;display: flex;flex-direction: column;justify-content: space-between;margin-bottom: 147rpx;}
	.shuru_box{height: 70rpx;display: flex;flex-direction: row;justify-content: space-between;}
	.shurutiao{height: 70rpx;width: 362rpx;background: #ededed;padding-left: 20rpx;}
	.biaoti{line-height: 70rpx;font-weight: bold;}
	
	.btn{width: 316rpx;height: 96rpx;background: url(../../static/img/a3.png) no-repeat center center;background-size: cover;border: none;outline: none;}
</style>
