<template>
	<view class="container">

		<add-tip :tip="tip" :duration="duration" />
		<v-tabs v-model="current" :tabs="tabs" @change="changeTab" class="tab"></v-tabs>
		<view class="coupon" ref="coupon">
			<view class="item" v-for="(v, i) in couponList" @click="toCoupon(i)" :key="i">
				<view class="top">
					<view class="left">
						<view class="content">
							<image :src="v.icon" class="icon" mode="widthFix" />
							<view class="name">{{ v.name }}</view>
						</view>
						<view class="text">{{ v.type }}</view>
					</view>
					<view class="right">点击领取</view>
				</view>
				<view class="content">
					<view>{{ v.desc }}</view>
				</view>
				<view class="bottom">
					<image :src="v.bannerPic" mode="widthFix" />
				</view>
			</view>
			<view style="height: 50px;"></view>
		</view>
		<view class="box">
			<view class="cu-bar tabbar bg-white">
				<navigator class="action" url="/pages/index/category">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/basics.png"></image>
					</view>
					<view class="text-gray">热榜</view>
				</navigator>
				<navigator class="action" url="/pages/index/news">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/component.png"></image>
					</view>
					<view class="text-gray">探索</view>
				</navigator>
				<navigator class="action" url="/pages/index/quan">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/coupon_cur.png"></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-green">优惠</view>
				</navigator>
				<navigator class="action" url="/pages/index/eatwhat">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/plugin.png"></image>
					</view>
					<view class="text-gray">帮我</view>
				</navigator>
				<navigator class="action" url="/pages/index/about">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/about.png"></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-gray">关于</view>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	import jWeixin from '../../node_modules/jweixin-module/lib/index.js'
	import addTip from "../../components/add-tip/add-tip.vue";
	
	export default {
		data() {
			return {
				current: 0,
				tabs: [],
				couponList: [],
				coupons: [],
				tip: "点击「分享」，下次访问更便捷",
				duration: 5,
				messages: [{
						"title": "美团饿了么大额红包，每日可领！"
					}, {
						"title": "吃了这么多年外卖，你知道这个秘密吗？"
					}, {
						"title": "这样点外卖，一年省下一个亿"
					}, {
						"title": "点外卖前先领券，吃霸王餐"
					}, {
						"title": "美团饿了么内部优惠券，手慢无"
					}, {
						"title": "点外卖不用优惠券，你就out了"
					}, {
						"title": "外卖不为人知的秘密，点这解密"
					}, {
						"title": "震惊！小伙点外卖竟然花了1分钱"
					},
					{
						"title": "从这点外卖，你也可以吃霸王餐"
					}
				]
			};
		},
		components: {
			addTip
		},
		onLoad() {
			this.getHome()
			//#ifdef H5
			let tabId = this.$route.query.tabId ? parseInt(this.$route.query.tabId) : 0
			//#endif
			for (let i in this.tabs) {
				if (tabId == this.tabs[i].tabId) {
					this.current = parseInt(i)
				}
			}
			this.changeTab(this.current)

			// #ifdef H5
			document.title = this.messages[Math.floor(Math.random() * this.messages.length)].title
			// #endif

			const url = window.location.href;

			uni.request({
				url: 'https://api.guoxiaorui.cn/wxsign/' + encodeURIComponent(url) + '/',
				success(res) {
					//通过微信config接口注入配置
					jWeixin.config({
						debug: false, //调试模式
						appId: res.data.appId, //必填，公众号的唯一标识
						timestamp: res.data.timestamp, //必填，生成签名的时间戳
						nonceStr: res.data.nonceStr, //必填，生成签名的随机串
						signature: res.data.signature, //必填，签名
						jsApiList: [
							'updateTimelineShareData',
							'updateAppMessageShareData'
						] //必填，需要使用的JS接口列表
					})

					window.share_config = { //自定义分享内容
						share: {
							imgUrl: 'https://news.guoxiaorui.cn/static/quan.png', //分享图标
							title: document.title, //分享标题
							desc: '大额外卖券、低价充话费、腾讯/爱奇艺/优酷会员~', //分享介绍
							link: url, //分享网址
							success: function(res) {
								// console.log(res)
							}
						}
					}
					jWeixin.ready(function() {
						console.log(share_config.share)
						jWeixin.updateTimelineShareData(share_config.share) //分享微信朋友圈
						jWeixin.updateAppMessageShareData(share_config.share) //分享微信好友
					})
				},
				fail(e) {
					console.log(e)
				}
			})

		},
		methods: {
			getHome() {
				uni.request({
					url: 'https://api.guoxiaorui.cn/quan',
					success: (res) => {
						// console.log(res.data)
						this.tabs = res.data.tabs
						this.coupons = res.data.coupons
						this.changeTab(0)
					}
				});
			},
			changeTab(index) {
				// console.log('当前选中的项：' + index);
				this.couponList = []
				uni.showLoading({
					title: '获取优惠中'
				});
				if (index == 0) {
					this.couponList = this.coupons
				} else {
					for (let i in this.coupons) {
						if (this.coupons[i].tabId == this.tabs[index].tabId) {
							this.couponList.push(this.coupons[i])
						}
					}
				}
				//#ifdef H5
				this.$nextTick(() => {
					this.$refs.coupon.scrollTop = 0;
				})
				//#endif
				setTimeout(() => {
					uni.hideLoading()
				}, 500)
			},
			toCoupon(i) {
				console.log(this.couponList[i])
				window.location.href = this.couponList[i].h5.path
			},
		}
	};
</script>

<style lang="scss">
	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}

	page {
		background-color: #f8f8f8;
	}


	.container {
		font-size: 14px;
		line-height: 24px;
		position: relative;

		.tab {
			position: fixed;
			top: var(--window-top);
			left: 0;
			z-index: 9999;
		}

		.coupon {
			padding-top: 200rpx;
			padding-bottom: 10rpx;

			.item {
				background-color: #ffffff;
				margin: 30rpx;
				border-radius: 10rpx;
				padding: 0 30rpx 30rpx 30rpx;

				.top {
					height: 116rpx;
					display: flex;
					align-items: center;
					justify-content: space-between;

					.left {
						height: 116rpx;
						width: 400rpx;
						display: flex;
						align-items: center;
						justify-content: space-between;

						.content {
							width: 100%;
						}

						.icon {
							display: inline-block;
							vertical-align: bottom;
							width: 52rpx;
							height: auto;
						}

						.name {
							text-align: left;
							display: inline-block;
							vertical-align: bottom;
							font-size: 34rpx;
							color: #000;
							line-height: 50rpx;
							font-weight: bold;
							margin-left: 15rpx;
						}

						.text {
							width: 150rpx;
							height: 38rpx;
							line-height: 38rpx;
							text-align: center;
							font-size: 24rpx;
							color: #61300e;
							background: linear-gradient(90deg, #f9db8d, #f8d98a);
							border-radius: 6rpx;
						}
					}

					.right {
						width: 170rpx;
						height: 60rpx;
						border-radius: 30rpx;
						background: linear-gradient(90deg, #ec6f43, #ea4a36);
						color: #fff;
						font-size: 28rpx;
						line-height: 60rpx;
						text-align: center;
					}
				}

				.bottom {
					height: 240rpx;
					width: 100%;

					image {
						display: block;
						width: 100%;
						height: 240rpx !important;
					}
				}
			}
		}
	}
</style>
