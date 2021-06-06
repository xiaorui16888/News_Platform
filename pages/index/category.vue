<template>
	<view>
		<h1 class="logo-title">胖妞热榜</h1>
		<p class='desc'>家事国事天下事，声声入耳</p>
		<view class="cu-bar search" hidden="true">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input @focus="InputFocus" @blur="InputBlur" :adjust-position="false" type="text" placeholder="搜索" confirm-type="search"></input>
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow-blur round">搜索</button>
			</view>
		</view>
		<view>
			<p class="category-header">综合</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=微博">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/s.weibo.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">新浪微博</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">热搜榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=知乎">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">知乎</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=微信">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/mp.weixin.qq.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">微信</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24h热文榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=百度">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/baidu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">百度</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 实时热点</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">科技</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=36氪">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/36kr.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">36氪</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">24小时热榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=少数派">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/sspai.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">少数派</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热门文章</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=虎嗅网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/huxiu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">虎嗅网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热文</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=IT之家">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/ithome.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">IT之家</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 日榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">娱乐</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=哔哩哔哩">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bilibili.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">哔哩哔哩</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">全站日榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=抖音">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/iesdouyin.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">抖音</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 视频榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=煎蛋">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/jandan.net.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">煎蛋</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24H热文</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=豆瓣小组">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/douban.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">豆瓣小组</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 讨论精选</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">社区</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=吾爱破解">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/52pojie.cn.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">吾爱破解</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">今日热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=百度贴吧">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/tieba.baidu.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">百度贴吧</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热议榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=天涯">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.tianya.cn.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">天涯</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热帖榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=虎扑社区">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.hupu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">虎扑社区</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 步行街热帖</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">购物</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=淘宝 ‧ 天猫">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/taobao.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">淘宝 ‧ 天猫</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">热销总榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=什么值得买">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/smzdm.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">什么值得买</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 好文原创榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=今日热卖">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/remai.today.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">今日热卖</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 全网线报聚合</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=拼多多">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/p.pinduoduo.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">拼多多</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 实时热销榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">财经</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=雪球">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/xueqiu.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">雪球</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">今日话题</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=第一财经">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/yicai.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">第一财经</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 新闻排行周榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=财新网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/caixin.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">财新网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 评论排行榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=新浪财经新闻">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/sina.com.cn.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">新浪财经新闻</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 点击量排行</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">大学</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=水木社区">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/newsmth.net.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">水木社区</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">十大热门话题</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=北大未名">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.pku.edu.cn.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">北大未名</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 全站热门话题</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=武大珞珈山水">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.whu.edu.cn.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">武大珞珈山水</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 十大热点话题</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=北师蛋蛋">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/oiegg.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">北师蛋蛋</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 十大话题</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">日报</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=知乎日报">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/daily.zhihu.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">知乎日报</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">Today</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=开眼视频">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/kaiyanapp.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">开眼视频</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 日报</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=百度知道日报">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/zhidao.baidu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">百度知道日报</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> Today</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=哔哩哔哩">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bilibili.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">哔哩哔哩</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 每周必看</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">地方门户</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=高楼迷">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/gaoloumi.cc.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">高楼迷</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">今日热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=苏州姑苏网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/gusuwang.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">苏州姑苏网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24小时热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=宽带山">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/kdslife.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">宽带山</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24小时热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=光谷社区">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/guanggoo.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">光谷社区</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 今日热议</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">影视</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=豆瓣电影">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/movie.douban.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">豆瓣电影</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">豆瓣新片榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=猫眼">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/maoyan.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">猫眼</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 国内票房榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=知乎">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">知乎</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 影视热榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=豆瓣电影">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/movie.douban.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">豆瓣电影</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 热门剧集排行榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">阅读</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=微信读书">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/weread.qq.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">微信读书</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">总榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=当当">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/book.douban.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">当当</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 畅销图书榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=起点中文网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/book.qidian.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">起点中文网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24小时热销榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=纵横中文网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/book.zongheng.com.png_50x50.png;">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">纵横中文网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24小时畅销榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">游戏</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=TapTap">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/taptap.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">TapTap</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">排行榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=3DM游戏网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/3dmgame.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">3DM游戏网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 最新新闻</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=机核网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/gcores.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">机核网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 每日最新</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=游研社">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/yystv.cn.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">游研社</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 首页推荐</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">体育</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=新浪体育新闻">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/sina.com.cn.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">新浪体育新闻</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">点击量排行</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=知乎">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/zhihu.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">知乎</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 体育热榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=虎扑社区">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.hupu.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">虎扑社区</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> NBA论坛热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=微信 ‧ 体育">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/mp.weixin.qq.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">微信 ‧ 体育</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 体育榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">产品</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=人人都是产品经理">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/woshipm.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">人人都是产品经理</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">热门文章</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=鸟哥笔记">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/niaogebiji.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">鸟哥笔记</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 周榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=产品100">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/chanpin100.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">产品100</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 周榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=Product Hunt">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/producthunt.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">Product Hunt</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 今日新产品</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">开发</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=GitHub">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/github.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">Github</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">Trending Today</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=CSDN论坛">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.csdn.net.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">CSDN论坛</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 技术区热帖</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=掘金">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/juejin.im.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">掘金</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 全站本周最热</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=开发者头条">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/toutiao.io.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">开发者头条</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 今日头条</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">应用</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=App Store">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/itunes.apple.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">App Store</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">中国iPhone免费榜</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=爱范儿">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/ifanr.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">爱范儿</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> AppSolution</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=最美应用">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/zuimeia.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">最美应用</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 每日最美</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=AppSo">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/app.so.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">AppSo</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 鲜面连线</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">汽车</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=汽车之家">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/club.autohome.com.cn.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">汽车之家</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">论坛精选日报</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=老司机">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/laosiji.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">老司机</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 24小时热门</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=易车网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/vc.yiche.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">易车网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 7日视频排行</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=太平洋汽车网">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.pcauto.com.cn.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">太平洋汽车网</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 帖子排行榜</view>
						</view>
					</view>
				</navigator>
			</view>
		</view>
		<view>
			<p class="category-header">安全</p>
			<view class="cu-list menu menu-avatar">
				<navigator class="cu-item arrow" url="/pages/index/news?category=先知社区">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/xz.aliyun.com.png_50x50.png);"></view>
					<view class="content">
						<view class="text-pink">
							<view class="text-cut">先知社区</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">精华推荐</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=看雪论坛">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/bbs.pediy.com.png_50x50.png);"></view>
					<view class="content">
						<view>
							<view class="text-cut">看雪论坛</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 最新精华</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=安全客">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/anquanke.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">安全客</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 最新</view>
						</view>
					</view>
				</navigator>
				<navigator class="cu-item arrow" url="/pages/index/news?category=FreeBuf" style="margin-bottom: 80px;">
					<view class="cu-avatar radius lg" style="background-image:url(https://file.ipadown.com/tophub/assets/images/media/freebuf.com.png_50x50.png);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">FreeBuf</view>

						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 最新</view>
						</view>
					</view>
				</navigator>
			</view>
			<view class="box">
				<view class="cu-bar tabbar bg-white">
					<navigator class="action" url="/pages/index/category">
						<view class="cuIcon-cu-image">
							<image src="/static/tabbar/basics_cur.png"></image>
						</view>
						<view class="text-green">热榜</view>
					</navigator>
					<navigator class="action" url="/pages/index/news">
						<view class="cuIcon-cu-image">
							<image src="/static/tabbar/component.png"></image>
						</view>
						<view class="text-gray">探索</view>
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
	</view>
</template>

<script>
</script>

<style>
	page {
		background-color: #fafafa;
	}

	.desc{
		margin-left: 25px;
	}
	
	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}

	.category-header {
		margin-top: .77em;
		margin-bottom: .3em;
		padding-left: 15px;
		padding-right: 15px;
		color: #999;
		font-size: 14px;
	}

	.logo-title {
		margin: 20px 30px 10px 20px;
	}
</style>
