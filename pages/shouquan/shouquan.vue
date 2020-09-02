<template>
	<view class="content">
		<image src="../../static/img/logo.png" mode="widthFix" class="logo"></image>
		<image src="../../static/img/b0.png" mode="widthFix" class="shouquan"></image>
		<view class="wenben">
			<view class="tongyi" @click="tongyi">
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			tongyi(){
				uni.redirectTo({
					url:'../shangchuan/shangchuan'
				})
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
	.shouquan{width: 650rpx;height: 44rpx;margin-bottom: 36rpx;}
	.wenben{width: 626rpx;height: 808rpx;background: url(../../static/img/b1.png) no-repeat center center;background-size: 100%;position: relative;}
	.tongyi{width: 124rpx;height: 44rpx;background: url(../../static/img/b2.png) no-repeat center center;background-size: cover;position: absolute;left: 50%;bottom: 23rpx;transform: translateX(-50%);}
</style>
