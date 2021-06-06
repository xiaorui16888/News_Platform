<template>
	<view>
		<view class="custom-info">
			<img alt="" class="custom-info-bg" :src="pic">
			<view class="custom-info-content">
				<view class="custom-top">
					<p class="ustom-subscribers">

					</p>
					<a class="custom-status" href="/">胖妞热榜</a>
				</view>
				<img alt="" class="custom-pic" :src="pic">
				<h1 class="custom-title">{{title}}</h1>
				<view>
					<view class="maintainer-info">
						<view class="official-topic-brief">232400 条数据 / 206818 人订阅 </div>
						</view>
					</view>
					<view class="follow-group">
						<a class="follow-node-btn weui-btn weui-btn_mini weui-btn_warn" href="javascript:;" nodeid="1" isfollow="0">
							订阅 </a>
					</view>
				</view>
			</view>
		</view>
		<div class="weui-panel__bd">
			<a :href="item.href" v-for="(item,index) in newsList" rel="nofollow" class="weui-media-box weui-media-box_appmsg">
				<div class="weui-media-box__bd">
					<h4 class="weui-media-box__title">{{index+1}}、{{item.title}}</h4>
				</div>
				<div class="weui-cell__ft"></div>
			</a>
		</div>
		<div class="weui-loadmore weui-loadmore_line"><span class="weui-loadmore__tips">最后更新于 1 分钟前</span>
		</div>
		<view style="height: 50px;">

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
						<image src="/static/tabbar/component_cur.png"></image>
					</view>
					<view class="text-green">探索</view>
				</navigator>
				<navigator class="action" url="/pages/index/quan">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/coupon.png"></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-gray">优惠</view>
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
	export default {
		data() {
			return {
				title: '',
				newsList: [],
				pic: "../../static/pangniu.png"
			};
		},
		methods: {
			onLoad: function(options) {
				if (options.category) {
					uni.request({
						url: this.websiteUrl+'/news/find_by_category_news/' + encodeURIComponent(options.category),
						// header: {
						// 	'content-type': 'application/json'
						// },
						success: (res) => {
							this.title = res.data.name
							this.newsList = res.data.list
							this.changePic(res.data.name);
						}
					});

				} else {
					uni.request({
						url: this.websiteUrl+'/news/random_news',
						// header: {
						// 	'content-type': 'application/json'
						// },
						success: (res) => {
							this.title = res.data.name
							this.newsList = res.data.list
							this.changePic(res.data.name);
						}
					});
				}
			},
			changePic(name) {
				if (name == "微博") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/s.weibo.com.png'
				} else if (name == "知乎") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png'
				} else if (name == "微信") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/mp.weixin.qq.com.png'
				} else if (name == "百度") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/baidu.com.png_50x50.png'
				} else if (name == "36氪") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/36kr.com.png'
				} else if (name == "少数派") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/sspai.com.png'
				} else if (name == "虎嗅网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/huxiu.com.png'
				} else if (name == "IT之家") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/ithome.com.png'
				} else if (name == "哔哩哔哩") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bilibili.com.png'
				} else if (name == "抖音") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/iesdouyin.com.png'
				} else if (name == "煎蛋") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/jandan.net.png'
				} else if (name == "豆瓣小组") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/douban.com.png'
				} else if (name == "吾爱破解") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/52pojie.cn.png'
				} else if (name == "百度贴吧") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/tieba.baidu.com.png'
				} else if (name == "天涯") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.tianya.cn.png'
				} else if (name == "虎扑社区") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.hupu.com.png'
				} else if (name == "淘宝 ‧ 天猫") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/taobao.com.png'
				} else if (name == "什么值得买") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/smzdm.com.png'
				} else if (name == "今日热卖") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/remai.today.png'
				} else if (name == "拼多多") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/p.pinduoduo.com.png'
				} else if (name == "雪球") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/xueqiu.com.png'
				} else if (name == "第一财经") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/yicai.com.png'
				} else if (name == "财新网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/caixin.com.png'
				} else if (name == "新浪财经新闻") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/sina.com.cn.png'
				} else if (name == "水木社区") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/newsmth.net.png'
				} else if (name == "北大未名") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.pku.edu.cn.png'
				} else if (name == "武大珞珈山水") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.whu.edu.cn.png'
				} else if (name == "北师蛋蛋") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/oiegg.com.png'
				} else if (name == "知乎日报") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/daily.zhihu.com.png'
				} else if (name == "开眼视频") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/kaiyanapp.com.png'
				} else if (name == "百度知道日报") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/zhidao.baidu.com.png'
				} else if (name == "哔哩哔哩") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bilibili.com.png'
				} else if (name == "高楼迷") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/gaoloumi.cc.png'
				} else if (name == "苏州姑苏网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/gusuwang.com.png'
				} else if (name == "宽带山") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/kdslife.com.png'
				} else if (name == "光谷社区") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/guanggoo.com.png'
				} else if (name == "豆瓣电影") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/movie.douban.com.png'
				} else if (name == "猫眼") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/maoyan.com.png'
				} else if (name == "知乎") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png'
				} else if (name == "豆瓣电影") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/movie.douban.com.png'
				} else if (name == "微信读书") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/weread.qq.com.png'
				} else if (name == "微信 ‧ 体育") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/mp.weixin.qq.com.png_50x50.png'
				} else if (name == "当当") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/book.douban.com.png'
				} else if (name == "起点中文网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/book.qidian.com.png'
				} else if (name == "纵横中文网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/book.zongheng.com.png'
				} else if (name == "TapTap") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/taptap.com.png'
				} else if (name == "3DM游戏网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/3dmgame.com.png'
				} else if (name == "机核网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/gcores.com.png'
				} else if (name == "游研社") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/yystv.cn.png'
				} else if (name == "新浪体育新闻") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/sina.com.cn.png'
				} else if (name == "知乎") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png'
				} else if (name == "虎扑社区") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.hupu.com.png'
				} else if (name == "新浪热点榜") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/rank.sinanews.sina.cn.png'
				} else if (name == "人人都是产品经理") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/woshipm.com.png'
				} else if (name == "鸟哥笔记") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/niaogebiji.com.png'
				} else if (name == "产品100") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/chanpin100.com.png'
				} else if (name == "Product Hunt") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/producthunt.com.png'
				} else if (name == "Github") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/github.com.png'
				} else if (name == "CSDN论坛") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.csdn.net.png'
				} else if (name == "掘金") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/juejin.im.png'
				} else if (name == "开发者头条") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/toutiao.io.png'
				} else if (name == "App Store") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/itunes.apple.com.png'
				} else if (name == "爱范儿") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/ifanr.com.png'
				} else if (name == "最美应用") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/zuimeia.com.png'
				} else if (name == "AppSo") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/app.so.png'
				} else if (name == "汽车之家") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/club.autohome.com.cn.png'
				} else if (name == "老司机") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/laosiji.com.png'
				} else if (name == "易车网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/vc.yiche.com.png'
				} else if (name == "太平洋汽车网") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.pcauto.com.cn.png'
				} else if (name == "先知社区") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/xz.aliyun.com.png'
				} else if (name == "看雪论坛") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/bbs.pediy.com.png'
				} else if (name == "安全客") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/anquanke.com.png'
				} else if (name == "FreeBuf") {
					this.pic = 'https://file.ipadown.com/tophub/assets/images/media/freebuf.com.png'
				}
			}
		}
	}
</script>

<style>
	page {
		background-color: #fafafa;
	}

	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}

	.weui-loadmore_line {
		border-top: 1px solid #e5e5e5;
		margin-top: 2.4em;
	}

	.weui-loadmore__tips {
		display: inline-block;
		vertical-align: middle;
	}

	.weui-loadmore_line .weui-loadmore__tips {
		position: relative;
		top: -.9em;
		padding: 0 .55em;
		background-color: #FAFAFA;
		color: #999;
	}

	.weui-loadmore {
		width: 65%;
		margin: 1.5em auto;
		line-height: 1.6em;
		font-size: 14px;
		text-align: center;
	}

	.weui-panel__bd {
		background-color: #fff;
	}

	a.weui-media-box {
		color: #000;
		-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
	}

	.weui-media-box:before {
		content: " ";
		position: absolute;
		left: 0;
		top: 0;
		right: 0;
		height: 1px;
		border-top: 1px solid #e5e5e5;
		color: #e5e5e5;
		-webkit-transform-origin: 0 0;
		transform-origin: 0 0;
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		left: 15px;
	}

	.weui-media-box_appmsg {
		display: -webkit-box;
		display: -webkit-flex;
		display: flex;
		-webkit-box-align: center;
		-webkit-align-items: center;
		align-items: center;
	}

	.weui-media-box {
		padding: 15px;
		position: relative;
	}

	.weui-media-box_appmsg .weui-media-box__bd {
		-webkit-box-flex: 1;
		-webkit-flex: 1;
		flex: 1;
		min-width: 0;
	}

	.weui-media-box__title {
		font-weight: 400;
		font-size: 17px;
		width: auto;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		word-wrap: normal;
		word-wrap: break-word;
		word-break: break-all;
	}

	.weui-media-box__desc {
		color: #999;
		font-size: 13px;
		line-height: 1.2;
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}

	a {
		text-decoration: none;
		-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
	}

	.follow-group {
		display: flex;
	}

	.logo-title {
		margin: 20px 30px 10px 20px;
	}

	.content-wrap {
		position: relative;
		overflow: hidden;
	}

	.custom-info {
		overflow: hidden;
		position: relative;
	}

	.custom-info-bg {
		position: absolute;
		z-index: 0;
		width: 100vw;
		-o-object-fit: contain;
		object-fit: contain;
	}

	.custom-info-content {
		position: relative;
		z-index: 1;
		background: rgba(0, 0, 0, .8);
		display: -webkit-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-orient: vertical;
		-webkit-box-direction: normal;
		-ms-flex-flow: column;
		flex-flow: column;
		-webkit-box-align: center;
		-ms-flex-align: center;
		align-items: center;
		color: #fff;
		padding: 15px;
		padding-bottom: 30px;
	}

	.custom-top {
		width: 100%;
		font-size: 12px;
		display: -webkit-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-pack: justify;
		-ms-flex-pack: justify;
		justify-content: space-between;
		-webkit-box-align: center;
		-ms-flex-align: center;
		align-items: center;
		margin-bottom: 15px;
	}

	.custom-pic {
		width: 80px;
		height: 80px;
		border-radius: 18px;
		border: 1px rgba(255, 255, 255, .3) solid;
		background: rgba(255, 255, 255, .3);
		margin-bottom: 20px;
	}

	.custom-status {
		border: 1px solid;
		border-radius: 4px;
		padding: 4px 10px;
		text-decoration: none;
		color: #fff;
	}

	.custom-title {
		min-height: 20px;
		font-size: 20px;
		font-weight: 700;
		margin-bottom: 15px;
	}

	.maintainer-info {
		width: 100%;
		font-size: 14px;
		margin-bottom: 20px;
	}

	.official-topic-brief {
		text-align: center;
		min-height: 16px;
		font-size: 16px;
		line-height: 24px;
		color: rgba(255, 255, 255, .8);
	}

	.weui-btn_mini {
		display: inline-block;
		padding: 0 1.32em;
		line-height: 2.3 !important;
		font-size: 13px !important;
	}

	.weui-btn_warn {
		background-color: #e64340;
	}

	.weui-btn {
		position: relative;
		margin-left: auto;
		margin-right: auto;
		padding-left: 14px;
		padding-right: 14px;
		box-sizing: border-box;
		font-size: 13px !important;
		text-align: center;
		text-decoration: none;
		color: #fff;
		line-height: 2.55555556;
		border-radius: 5px;
		-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
		overflow: hidden;
	}

	.weui-btn:after {
		content: " ";
		width: 200%;
		height: 200%;
		position: absolute;
		top: 0;
		left: 0;
		border: 1px solid rgba(0, 0, 0, .2);
		-webkit-transform: scale(.5);
		transform: scale(.5);
		-webkit-transform-origin: 0 0;
		transform-origin: 0 0;
		box-sizing: border-box;
		border-radius: 10px;
	}
</style>
