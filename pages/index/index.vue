<template>
	<view class="content">
		<image class="logo" src="../../static/logo.png"></image>
		<view>
			<text class="title">{{title}}</text>
		</view>
		<view class="uni-list">
			<view class="uni-list-cell" v-for="(item,index) in btnTitles" :key="index">
				<button class="uni-list-cell-navigate uni-navigate-right" @click="btnclick(index)">
					{{item}}
				</button>
			</view>
		</view>
		<text>{{result}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '阿里百川UniApp插件',
				btnTitles: ['百川初始化', '授权并登录', '用户是否已登录', '退出登录', '跳转到店铺', '跳转到商品', '领取优惠券'],
				result: '',
			}
		},
		onLoad() {

		},
		methods: {
			btnclick: function(e) {
				const bcPlugin = uni.requireNativePlugin('baichuanplugin');
				switch (e) {
					case 0:
						bcPlugin.BCSDKInitWithCallback(result => {
							uni.showModal({
								title:'百川初始化',
								content:'code:'+result['code'] + '\nmessage:' + result['message']
							})
						});
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 1:
						bcPlugin.BCAuth(result => {
							// userInfo字典：nick、avatarUrl、openId、openSid、topAuthCode、topAccessToken
							uni.showModal({
								title:'授权登录',
								content:'code:'+result['code'] + '\nmessage:' + result['message'] + '\n用户信息：'+ result['userInfo']['nick']
							})
						});
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 2:
						bcPlugin.BCIsUserLogin(result => {
								uni.showModal({
									title:'用户是否登录',
									content:'code:'+result['code'] + '\nmessage:' + result['message']
								})
							});
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 3:
						uni.showModal({
							title:'请联系作者',
							content:'请联系作者'
						})
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 4:
						uni.showModal({
							title:'请联系作者',
							content:'请联系作者'
						})
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 5:
						uni.showModal({
							title:'请联系作者',
							content:'请联系作者'
						})
						this.result = '点击了：' + this.btnTitles[e];
						break;
					case 6:
						uni.showModal({
							title:'请联系作者',
							content:'请联系作者'
						})
						this.result = '点击了：' + this.btnTitles[e];
						break;
					default:
						break;
				}
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 20upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
