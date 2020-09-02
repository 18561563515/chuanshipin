<template>
	<view class="content">
		<image src="../../static/img/logo.png" mode="widthFix" class="logo"></image>
		<image src="../../static/img/d1.png" mode="widthFix" class="chenggong"></image>
		<!-- <image src="../../static/img/d2.png" mode="widthFix" class="ditu"></image> -->
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
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
		background: url(../../static/img/BG3.jpg) no-repeat center bottom;
		background-size: 100% auto;
		padding-top: 47rpx;
	}
	
	.logo{width: 666rpx;height: 98rpx;margin-bottom: 72rpx;}
	.chenggong{width: 538rpx;height: 538rpx;}
	.ditu{width: 488rpx;height: 426rpx;position: absolute;bottom: 110rpx;left: 52rpx;}
</style>
