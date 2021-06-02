<template>
	<view>
		<h1 class="logo-title">关于</h1>
		<view class='margin-xl bg-white padding-xl radius shadow-lg'>
			<view class='text-center margin-bottom text-lg  text-grey'>关于胖妞热榜</view>
			<view class='text-content'>
				<view>Hi！朋友~欢迎使用<font style="font-weight: 800;color: green;">胖妞热榜</font>！</view>
				<view class='margin-top-sm'>该项目是我个人开发的一款简约版的新闻展示类程序。这个项目聚合了互联网多平台的热榜头条，足以做到“家事国事天下事，声声入耳”。</view>
				<view class='margin-top-sm'>项目是开源的，不收取任何费用，如果这个项目有帮到你，或者你觉得很赞，可以在<a href="https://github.com/xiaorui16888/News_Platform">GitHub</a>里扫描赞赏码支持一下！</view>
				<view class='margin-top-sm'>并且该项目所用到的API，都是自开发的。无使用次数限制，传输速度极快。٩(๑❛ᴗ❛๑)۶</view>
				<view class="margin-top-sm">作者我也是花了时间和精力的，开放的API是免费的，我不希望一些“无心人”对接口进行流量攻击~</view>
				<view class='margin-top-sm'>更多功能，敬请期待！</view>
				<view class='margin-top-sm'>微信：iamyangxuea</view>
			</view>
			<image src="../../author.png"></image>
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
				<navigator class="action" url="/pages/index/api">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/plugin.png"></image>
					</view>
					<view class="text-gray">API</view>
				</navigator>
				<navigator class="action" url="/pages/index/about">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/about_cur.png"></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-green">关于</view>
				</navigator>
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

	.logo-title {
		margin: 20px 30px 10px 20px;
	}

	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}
</style>
