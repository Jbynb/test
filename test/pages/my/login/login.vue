<!-- 蓝色登录页面2 -->
<template>
	
	<view class="font">
		<view class="top"></view>
		<view class="login-view" style="">
			<view class="t-login">
				<view class="login_text">
					账号登录
				</view>
				<form class="cl">
					<view class="t-a">
						<input type="text" name="phone" placeholder="请输入账号" v-model="loginInfo.phone" />
					</view>
					<view class="t-a">
						<input type="password" name="password"  placeholder="请输入密码" v-model="loginInfo.password" />
					</view>
					<view class="t-a flex">
						<view class="inp">
							<input type="text" name="captcha" maxlength="4" placeholder="请输入验证码" v-model="loginInfo.captcha" />
						</view>
						<view class="codeImage" span="4">
							<image  :src="codeImage" width="100%"   @click="getImageCode"></image>
						</view>
					</view>
					<button @tap="login()">登 录</button>
					<view class="reg" @tap="reg()">注 册</view>
				</form>
			</view>
		</view>
	</view>
</template>
<script>
	export default {

		data() {
			return {
				loginInfo:{
					phone: '', //手机号码
					password: '', //密码
					captcha:'',
				},
				
			};
		},
		onLoad() {
			
		},
		methods: {
			
			reg(){
				uni.navigateTo({url:"/pages/my/register/register"})
			},
			login(){
				let that = this;
				if (!that.loginInfo.phone) {
					uni.showToast({
						title: '请输入您的账号',
						icon: 'none'
					});
					return;
				}
				if (!that.loginInfo.password) {
					uni.showToast({
						title: '请输入您的密码',
						icon: 'none'
					});
					return;
				}
				if (!that.loginInfo.captcha) {
					uni.showToast({
						title: '请输入您的验证码',
						icon: 'none'
					});
					return;
				}
				
			}
			
		
		
		}
	};
</script>
<style lang="scss" scoped>
	.top {
	  display: flex;
	  flex-direction: row;
	  justify-content: space-between;
	  align-items: center;
	  position: fixed;
	  top: 0;
	  left: 0;
	  width: 100%;
	  height: 300rpx;
	  background: linear-gradient(90deg, #2870e5 0, #2870e5 45%, #2870e5);
	}
	.txt {
		font-size: 32rpx;
		font-weight: bold;
		color: #333333;
	}
	.flex{
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	.login_text {
		font-size: 40rpx;
		font-weight: 500;
		color: #333333;
		position: relative;
		padding-bottom: 20rpx;
		margin-bottom: 90rpx;
		
	}
	.inp{
		width: calc(100% - 200rpx);
	}
	.codeImage{
		width: 200rpx;
		height: 80rpx;
		background-color: #ddd;
		image{
			width: 100%;
			height: 100%;
		}
	}

	.img-a {
		width: 100%;
		height: 699rpx;
		
		background-size: 100%;
	}

	.reg {
		font-size: 28rpx;
		color: #fff;
		height: 90rpx;
		line-height: 90rpx;
		border-radius: 50rpx;
		font-weight: bold;
		background: #f5f6fa;
		color: #000000;
		text-align: center;
		margin-top: 30rpx;
	}

	.login-view {
		width: 91.3%;
		margin: 0 auto;
		position: relative;
		margin-top: 100rpx;
		background-color: #ffffff;
		border-radius: 10rpx;
	}

	.t-login {
		width: 100%;
		box-sizing: border-box;
		font-size: 28rpx;
		padding: 80rpx 30rpx;
	}

	.t-login button {
		font-size: 28rpx;
		background: #2796f2;
		color: #fff;
		height: 90rpx;
		line-height: 90rpx;
		border-radius: 50rpx;
		font-weight: bold;
	}

	.t-login input {
		height: 90rpx;
		line-height: 90rpx;
		margin-bottom: 20rpx;
		border-bottom: 1px solid #E4E4E4;
		font-size: 28rpx;
	}

	.t-login .t-a {
		position: relative;
		font-size: 32rpx;
	}

	.t-b {
		text-align: left;
		font-size: 42rpx;
		color: #ffffff;
		padding: 130rpx 0 0 70rpx;
		font-weight: bold;
		line-height: 70rpx;
	}

	.t-login .t-c {
		position: absolute;
		right: 22rpx;
		top: 22rpx;
		background: #5677fc;
		color: #fff;
		font-size: 24rpx;
		border-radius: 50rpx;
		height: 50rpx;
		line-height: 50rpx;
		padding: 0 25rpx;
	}

	.t-login .t-d {
		text-align: center;
		color: #999;
		margin: 80rpx 0;
	}

	.t-login .t-e {
		text-align: center;
		width: 250rpx;
		margin: 80rpx auto 0;
	}

	.t-login .t-g {
		float: left;
		width: 50%;
	}

	.t-login .t-e image {
		width: 50rpx;
		height: 50rpx;
	}

	.t-login .t-f {
		text-align: center;
		margin: 150rpx 0 0 0;
		color: #666;
	}

	.t-login .t-f text {
		margin-left: 20rpx;
		color: #aaaaaa;
		font-size: 27rpx;
	}

	.t-login .uni-input-placeholder {
		color: #C0C4CC;
	}

	.cl {
		zoom: 1;
	}

	.cl:after {
		clear: both;
		display: block;
		visibility: hidden;
		height: 0;
		content: '\20';
	}
</style>
