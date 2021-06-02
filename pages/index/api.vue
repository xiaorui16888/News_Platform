<template>
	<view>
		<MDParserHighlight :resource="str" style="margin: 10px;"></MDParserHighlight>
		<view style="height: 50px;"></view>
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
						<image src="/static/tabbar/plugin_cur.png"></image>
					</view>
					<view class="text-green">API</view>
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
	import MDParserHighlight from '../../components/cmder-MDParserHighlight/index.vue'
	export default {
		components: {
			MDParserHighlight
		},
		data(){
			return {
				str:''
			}
		},
		methods:{
			onLoad(){
				uni.request({
					url:'https://guoxiaorui.cn/md/',
					success: (res) => {
						this.str=res.data
					}
				})
				
				
			}
		}

	}
</script>

<style>
	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}
</style>
