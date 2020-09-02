<template>
	<view class="content">
		<image src="../../static/img/logo.png" mode="widthFix" class="logo"></image>
		<image src="../../static/img/c1.png" mode="widthFix" class="biaoti"></image>
		<view class="rongqi" @tap="upload">
			
		</view>
		<view class="mask" v-if="maskshow">
			<view class="xinxi">
				<text>正在上传视频：{{jindu}}%</text>
				<text>请勿关闭页面</text>
			</view>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				jindu:0,
				maskshow:false
			}
		},
		methods: {
			upload(){
				var that = this
				uni.chooseVideo({
					sourceType:['album', 'camera'],
					success(chooseImageRes) {
						var vid = uni.getStorageSync('shipinid')
						var shijian = new Date().getTime()
						const tempFilePaths = chooseImageRes.tempFilePath;
						
						if (chooseImageRes.size>40000000) {
							uni.showModal({
								content: '视频最大40M',
								showCancel: true
							});
						} else{
							/* uni.showLoading({
								title:this.jindu,
								mask:true
							}) */
							that.maskshow = !that.maskshow
							console.log(tempFilePaths)
							const uploadTask = uni.uploadFile({
							            url: 'http://3w.donglianguoji.com/app/chuanshipin/php/shipin.php', //仅为示例，非真实的接口地址
							            filePath: tempFilePaths,
							            name: 'file',
							            formData: {
							                'userid': vid,
											'shijian':shijian
							            },
							            success: (uploadFileRes) => {
							                console.log(uploadFileRes.data);
							            }
							        });
							uploadTask.onProgressUpdate((res) => {
							            console.log('上传进度' + res.progress);
										that.jindu = res.progress
							            // console.log('已经上传的数据长度' + res.totalBytesSent);
							            // console.log('预期需要上传的数据总长度' + res.totalBytesExpectedToSend);
										if (res.progress>=100) {
											// uni.hideLoading()
											uni.redirectTo({
												url:'../chenggong/chenggong'
											})
										}
							            
							        });
						}
					}
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
	
	.logo{width: 666rpx;height: 98rpx;margin-bottom: 96rpx;}
	.biaoti{width: 474rpx;height: 130rpx;margin-bottom: 164rpx;}
	.rongqi{width: 424rpx;height: 116rpx;background: url(../../static/img/c2.png) no-repeat center center;background-size: cover;}
	
	.mask{position: absolute;top: 0;left: 0;bottom: 0;right: 0;background: rgba(0,0,0,.7);z-index: 10;display: flex;flex-direction: column;justify-content: center;align-items: center;}
	.xinxi{padding: 25rpx 40rpx;display: flex;flex-direction: column;justify-content: center;align-items: center;background: #fff;border-radius: 20rpx;}
	.xinxi>text{line-height: 60rpx;color: #DD524D;}
</style>
