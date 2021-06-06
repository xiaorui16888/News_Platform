<template>
	<view>
		<view :class="status" id="bg"></view>
		<view id="tempContainer">
			<view v-for="(item, index) in tempFoods" :key="index" :animation="handleAnimationEnd" class="tempItem" :data-id="item.id"
			 :style="'top:' + item.top + ';left:' + item.left + ';font-size:' + item.fontSize + ';color:' + item.color">
				{{item.food}}
			</view>
		</view>
		<view id="outer">
			<view id="inner" style="margin-top: 20px">
				<view :class="status + ' ' + (restaurants.length?'restaurants':'')" id="main">
					<text class="tip">点击可以切换饭点~</text>
					<view :animation="titleAnimationData" @tap="changeTime" class="title">今天<text class="time">{{menu[menuIdx][0]}}</text>吃<text
						 class="what">{{food}}</text>
						<text class="punctuation">{{punctuation}}</text>
					</view>
					<view @tap="play" id="startBtn">
						<view class="inner">{{btnText}}</view>
					</view>
					<!-- #ifdef MP-WEIXIN -->
					<view class="share">
						<button id="shareApp" open-type="share">
							<view class="inner">分享吃什么</view>
						</button>
						<button id="luckyMoney" @tap="getLuckyMoney">
							<view class="inner">去领红包</view>
						</button>
					</view>
					<!-- #endif -->
					<text @tap="showRestaurant" id="showRestaurant">查看餐厅详情</text>
				</view>
				<view :class="status==='running'?'hide':''" id="footer">
					<view id="toggle">
						<text @tap="changeType" :class="'option ' + (type==='human'?'selected':'')" data-type="human" id="human">正常人类</text>
						<text @tap="changeType" :class="'option ' + (type==='monster'?'selected':'')" data-type="monster" id="monster">非正常人类</text>
						<view :class="'hb ' + type"></view>
					</view>
					<!-- 	<view @tap="showLocationMenu" class="fab" id="getRestaurants" title="定位餐厅"></view>
					<view @tap="editMenu" class="fab" id="editMenu" title="菜单"></view> -->
				</view>
			</view>
			<view class="safeAreaInsetBottom"></view>
		</view>
		<view id="menuModal" v-if="showMenu">
			<form @submit="handleFormSubmit" style="margin-top:20px">
				<text class="title">~ 想吃什么 ~</text>
				<textarea maxlength="1000" name="textarea" placeholder="在这里输入菜单,项目间以空格分隔,保存后会缓存到本地,再次打开会恢复初始值…" :value="menuValue"></textarea>
				<button form-type="submit">保存，再次打开恢复默认</button>
			</form>
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
						<image src="/static/tabbar/coupon.png"></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-gray">优惠</view>
				</navigator>
				<navigator class="action" url="/pages/index/eatwhat">
					<view class="cuIcon-cu-image">
						<image src="/static/tabbar/plugin_cur.png"></image>
					</view>
					<view class="text-green">帮我</view>
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
	function t(t, a, e) {
		return a in t ? Object.defineProperty(t, a, {
			value: e,
			enumerable: !0,
			configurable: !0,
			writable: !0
		}) : t[a] = e, t;
	}
	var a = new(require("../../libs/qqmap-wx-jssdk.min.js"))({
			key: "HRRBZ-SMFLJ-WZJFE-KWLZG-IOYCF-BEFNL"
		}),
		e = new Date().getHours(),
		n = uni.getSystemInfoSync()

	export default {
		data() {
			return {
				menu: [
					["早饭",
						"面包 蛋糕 荷包蛋 烧饼 饽饽 肉夹馍 油条 馄饨 火腿 面条 小笼包 玉米粥 肉包 煎饼果子 饺子 煎蛋 烧卖 生煎 锅贴 包子 酸奶 苹果 梨 香蕉 皮蛋瘦肉粥 蛋挞 南瓜粥 煎饼 玉米糊 泡面 粥 馒头 燕麦片 水煮蛋 米粉 豆浆 牛奶 花卷 豆腐脑 煎饼果子 小米粥 黑米糕 鸡蛋饼 牛奶布丁 水果沙拉 鸡蛋羹 南瓜馅饼 鸡蛋灌饼 奶香小馒头 汉堡包 披萨 八宝粥 三明治 蛋包饭 豆沙红薯饼 驴肉火烧 粥 粢饭糕 蒸饺 白粥"
						.split(" ")
					],
					["午饭",
						"盖浇饭 砂锅 大排档 米线 满汉全席 西餐 麻辣烫 自助餐 炒面 快餐 水果 西北风 馄饨 火锅 烧烤 泡面 水饺 日本料理 涮羊肉 味千拉面 面包 扬州炒饭 自助餐 菜饭骨头汤 茶餐厅 海底捞 西贝莜面村 披萨 麦当劳 KFC 汉堡王 卡乐星 兰州拉面 沙县小吃 烤鱼 烤肉 海鲜 铁板烧 韩国料理 粥 快餐 萨莉亚 桂林米粉 东南亚菜 甜点 农家菜 川菜 粤菜 湘菜 本帮菜 全家便当"
						.split(" ")
					],
					["晚饭",
						"盖浇饭 砂锅 大排档 米线 满汉全席 西餐 麻辣烫 自助餐 炒面 快餐 水果 西北风 馄饨 火锅 烧烤 泡面 水饺 日本料理 涮羊肉 味千拉面 面包 扬州炒饭 自助餐 菜饭骨头汤 茶餐厅 海底捞 西贝莜面村 披萨 麦当劳 KFC 汉堡王 卡乐星 兰州拉面 沙县小吃 烤鱼 烤肉 海鲜 铁板烧 韩国料理 粥 快餐 萨莉亚 桂林米粉 东南亚菜 甜点 农家菜 川菜 粤菜 湘菜 本帮菜 全家便当"
						.split(" ")
					]
				],
				menuIdx: e < 9 || e >= 23 ? 0 : e < 13 ? 1 : 2,
				doubi: "冰箱 书桌 电扇 空调 马桶 翔 鼠标 键盘 显示器 电视 台灯 饭盒 iPad iPhone 手机 餐巾纸 电话 椅子 纸箱 窗帘 插座 被单 报纸 杂志 相框 照片 衣服 内裤 内衣 袜子 妹子 汉子 砖头 混凝土 钢筋 塑料袋 衣架 书 手环 手表 鼠标垫 眼药水 跑车 自行车 三轮车 坦克 潜水艇 飞机 火箭 U盘 CPU 显卡 刀片 碎玻璃 圆珠笔 钢笔 交通卡 银行卡 身份证 户口簿 橡皮筋 双面胶 502胶水 订书机 螺丝刀 锤子 榔头 垃圾桶 花花草草 树皮 洗手液 妇炎洁 姨妈巾 哆啦A梦 仙人掌 企鹅 大熊猫 穿山甲 米老鼠 唐老鸭 跳跳虎 旅行箱 DVD 音响 热水器 热水袋 电热棒 电池 充电器 相机 自拍杆 耳机 吊灯 雨伞 钱包 鞋子 人字拖 床垫 绣花针 戒指 窨井盖 路灯 主板 程序猿 工程狮 电线 摄像头 西北风 生活 路由器 洗手液 沐浴露 肥皂 羽毛球拍 保龄球 皮带 皮鞭 电池 牙膏 手电筒 瑜伽垫 假发 82年的自来水 马蜂窝 瑞士军刀 地板 水管 电钻"
					.split(" "),
				os: "大哥，饶命啊大哥 吃吃吃，就知道吃 壮士，干了这碗热翔 就这，还不够我塞牙缝儿 莫慌，抱紧我 吃一个，长一斤 你帅你先吃 你胖你先吃 听说吃这玩意吃不胖 你先吃，我不饿 不吃不是中国人 配上鸡汤，口味更佳 我仿佛看到了盐水瓶 嗯，好吃么？ 饭后注意漱口哦 这菜红烧味道如何？ 饭后百步走，活到九十九 分享页面到朋友圈，可以获得30个QQ太阳 据说吃完99%都哭了 惊天内幕！这网页是逗你玩的 为了身边的朋友！！转！！！！ 我也是醉了 我想静静，不要问我静静是谁 解决吃什么难题哪家强？ 我就笑笑不说话 转发过100，然并卵 活到老，吃到老 我给你讲个笑话 你别哭喔 你知道怎样得精神分裂症吗？那样我就再不是一个人了。 天下没有不散的筵席。我都还没吃完，你们都走了。 吃不到的醋，最酸。 躲了一辈子的雨，雨会不会很难过 小猪一定不知道自己的肉很好吃吧，真替它们心酸。 作为一个胖子，居然还自称自己不是个粗人！ 心情不好就吃吃吃 念念不忘，必会下单 好吃不如饺子，好玩不过嫂子 别低头，哈喇子会掉 今晚我们都是吃货 我这叫圆润，不叫胖 这不叫胖，叫丰满！ 吃饭前记得用手机消消毒 集满20个赞，明天早起瘦10斤 好吃的不要不要的 不好吃，不要钱 吃的我蹲下起立就头晕 听说你是广东人？ 贝爷，卒。"
					.split(" "),
				menuValue: "",
				showMenu: !1,
				type: "human",
				foods: [],
				tempFoods: [],
				restaurants: [],
				status: "idle",
				food: "神马",
				punctuation: "？",
				btnText: "开始",
				titleAnimationData: {}
			};
		},
		components: {},
		props: {},
		onLoad: function() {
			const storFoods = uni.getStorageSync("menu-" + this.menuIdx);
			if (storFoods) {
				this.setData({
					foods: storFoods
				});
			} else {
				this.setData({
					foods: this.menu[this.menuIdx][1]
				});
			}
			// #ifdef H5
			document.title = '今早、中、晚吃什么？'
			// #endif

		},
		methods: {
			setData: function(obj) {
				let that = this;
				let keys = [];
				let val, data;
				Object.keys(obj).forEach(function(key) {
					keys = key.split('.');
					val = obj[key];
					data = that.$data;
					keys.forEach(function(key2, index) {
						if (index + 1 == keys.length) {
							that.$set(data, key2, val);
						} else {
							if (!data[key2]) {
								that.$set(data, key2, {});
							}
						}
						data = data[key2];
					})
				});

			},
			random: function(t, a) {
				return t = t || 100, a = a || 0, Math.floor(Math.random() * (t - a + 1)) + a;
			},
			handleAnimationEnd: function(t) {
				var a = Number(t.target.dataset.id);
				this.tempFoods.splice(this.tempFoods.findIndex(function(t) {
					return t.id === a;
				}), 1), this.setData({
					tempFoods: this.tempFoods
				});
			},
			play: function() {
				var a = this;
				console.log(a.foods)
				if ("running" === this.status) clearTimeout(this.timer), this.setData({
					status: "done",
					punctuation: "！",
					btnText: "换一个"
				}), "monster" === this.type && uni.showToast({
					title: this.os[this.random(this.os.length - 1)],
					icon: "none"
				});
				else {
					var e = 1;
					a.setData({
						status: "running",
						tempFoods: [],
						punctuation: "？"
					});
					! function n() {
						var i,
							s = a.foods[a.random(a.foods.length - 1)];
						var ha = "tempFoods[" + a.tempFoods.length + "]";
						console.log(ha)
						a.setData(
							i = {},
							t(i, "food", s),
							t(i, "btnText", "停"), i,
							a.tempFoods.push({
								id: e,
								food: s,
								top: a.random(100, 0) + "%",
								left: a.random(100, 0) + "%",
								fontSize: a.random(37, 14) + "px",
								color: 'rgba(0,0,0," + a.random(7, 3) / 10 + ")'
							})
						);

						console.log(i)
						e++, a.timer = setTimeout(n, 60);
					}();
				}

			},
			getLuckyMoney: function() {
				wx.switchTab({
					url: '/pages/index/index' //实际路径要写全
				});
			},
			changeType: function(t) {
				var a = t.target.dataset.type;
				a !== this.type && (this.setData({
					type: a,
					food: "神马",
					punctuation: "？",
					btnText: "开始",
					foods: "human" === a ? this.menu[this.menuIdx][1] : this.doubi,
					restaurants: []
				}), uni.showToast({
					title: "monster" == a ? "注意！前方高能！" : "还是人类好吃呢Ψ(￣∀￣)Ψ",
					icon: "none"
				}), uni.reportAnalytics("toggle_type", {
					type: a
				}));
			},
			changeTime: function(t) {
				if ("running" !== this.status) {
					var a = "number" == typeof t ? t : (this.menuIdx + 1) % this.menu.length;
					this.setData({
						menuIdx: a,
						foods: this.menu[a][1],
						food: "神马",
						punctuation: "？",
						btnText: "开始",
						restaurants: []
					}), this.animation = uni.createAnimation({
						duration: 70,
						timingFunction: "linear"
					});

					for (var e = [5, -10, 15, -20, 15, -10, 0], n = 0; n < e.length; n++) this.animation.translateX(e[n]).step();

					this.setData({
						titleAnimationData: this.animation.export()
					}), uni.reportAnalytics("toggle_time", {
						time: this.menu[this.menuIdx][0]
					});
				}
			},
			searchRestaurants: function(t, e) {
				return new Promise(function(n, i) {
					a.search({
						location: t,
						keyword: "美食",
						page_size: 20,
						page_index: e,
						success: n,
						fail: i
					});
				});
			},
			showLocationMenu: function() {
				var t = this;
				uni.showActionSheet({
					itemList: ["获取附近餐厅", "手动定位地址"],
					success: function(a) {
						switch (a.tapIndex) {
							case 0:
								t.getRestaurants();
								break;

							case 1:
								uni.chooseLocation({
									success: t.getRestaurants
								});
						}

						uni.reportAnalytics("get_restaurants", {
							type: 0 === a.tapIndex ? "nearby" : "locate"
						});
					}
				});
			},
			getRestaurants: function(t) {
				var a = this;
				uni.showLoading({
					title: t ? "搜索美食中…" : "获取附近美食…",
					mask: !0
				}), Promise.all(Array.from({
					length: 3
				}, function(e, n) {
					return a.searchRestaurants(t, n + 1);
				})).then(function(t) {
					var e = t.reduce(function(t, a) {
						return t.concat(a.data);
					}, []);

					a.setData({
						type: "human",
						food: "神马",
						punctuation: "？",
						btnText: "开始",
						restaurants: e,
						foods: e.map(function(t) {
							return t.title;
						}),
						status: "idle"
					}), setTimeout(function() {
						uni.showToast({
							title: "菜单已更新"
						});
					}, 10);
				}, function(t) {
					setTimeout(function() {
						uni.showToast({
							title: JSON.stringify(t),
							icon: "none"
						});
					}, 10);
				}).then(function() {
					return uni.hideLoading();
				});
			},
			showRestaurant: function() {
				var t = this,
					a = this.restaurants.find(function(a) {
						return a.title === t.food;
					});
				uni.openLocation({
					latitude: a.location.lat,
					longitude: a.location.lng,
					name: a.title,
					address: a.address
				});
			},
			editMenu: function() {
				this.setData({
					showMenu: !0,
					menuValue: (this.restaurants.length ? this.restaurants.map(function(t) {
						return t.title;
					}) : "human" === this.type ? this.menu[this.menuIdx][1] : this.doubi).join(" ")
				});
			},
			handleFormSubmit: function(t) {
				var a = t.detail.value.textarea.trim();
				if (a) {
					this.setData({
						showMenu: !1,
						foods: a.split(" ")
					});
					uni.setStorage({
						key: "menu-" + this.menuIdx,
						data: a.split(" ")
					});
				} else {
					uni.showToast({
						title: "啥也没有，吃西北风去啊？",
						icon: "none"
					});
				}

			}
		}
	};
</script>
<style>
	.box {
		position: fixed;
		width: 100%;
		bottom: 0px;
		box-shadow: 19px 3px 20px 0px #f0f0f0;
	}

	#bg {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: -1;
		background: #e9e9e9 url("data:image/png;base64,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");
		transform: translateZ(0);
		animation: flow 16s linear infinite;
	}

	#bg.running {
		animation-play-state: paused;
	}

	@-webkit-keyframes flow {
		0% {
			background-position: 50% 0;
		}

		to {
			background-position: 50% -300px;
		}
	}

	@keyframes flow {
		0% {
			background-position: 50% 0;
		}

		to {
			background-position: 50% -300px;
		}
	}

	#outer {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
	}

	#inner {
		position: relative;
		flex: 1;
	}

	.adContainer {
		width: 100%;
		max-width: 414px;
		align-self: center;
	}

	.safeAreaInsetBottom {
		height: env(safe-area-inset-bottom);
	}

	#main {
		position: relative;
		margin-top: 20%;
		text-align: center;
	}

	.title {
		margin: 0 0 30px;
		padding: 0;
		font-weight: 400;
		font-size: 32px;
		cursor: pointer;
		color: #333;
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}

	.what {
		font-weight: 700;
		color: #111;
	}

	#main.restaurants {
		margin-top: 40%;
	}

	#main.restaurants .what {
		display: block;
	}

	#main.restaurants.done .what {
		white-space: normal;
	}

	#showRestaurant {
		display: none;
		margin-top: 50px;
		font-size: 12px;
		color: #333;
		border-bottom: 1px dotted;
	}

	#main.restaurants.done #showRestaurant {
		display: inline-block;
	}

	.tip {
		position: absolute;
		top: -50px;
		left: 50%;
		padding: 7px 12px;
		background: rgba(0, 0, 0, .6);
		color: #fff;
		white-space: nowrap;
		border-radius: 15px;
		background-size: contain;
		transform: translate3d(-50%, 0, 0);
		animation: tip 3s linear 1s both;
	}

	@-webkit-keyframes tip {

		0%,
		to {
			opacity: 0;
			transform: perspective(600px) translate3d(-50%, 7px, 0) scale(.7) rotateY(180deg);
		}

		20%,
		80% {
			opacity: 1;
			transform: perspective(600px) translate3d(-50%, 0, 0) rotateY(0deg);
		}
	}

	@keyframes tip {

		0%,
		to {
			opacity: 0;
			transform: perspective(600px) translate3d(-50%, 7px, 0) scale(.7) rotateY(180deg);
		}

		20%,
		80% {
			opacity: 1;
			transform: perspective(600px) translate3d(-50%, 0, 0) rotateY(0deg);
		}
	}

	.tip:after {
		content: "";
		position: absolute;
		top: 100%;
		left: 50%;
		margin-left: -4px;
		border: 8px solid transparent;
		border-top-color: rgba(0, 0, 0, .6);
	}

	#startBtn {
		width: 190px;
		height: 70px;
		margin: 0 auto;
		padding: 5px;
		border-radius: 40px;
		background: rgba(0, 0, 0, .1);
		box-shadow: inset 0 2px 3px rgba(0, 0, 0, .07), 0 1px hsla(0, 0%, 100%, .5);
	}

	#startBtn .inner {
		width: 100%;
		height: 100%;
		line-height: 60px;
		color: #fff;
		font-size: 28px;
		text-align: center;
		text-shadow: 0 1px 2px rgba(0, 0, 0, .3);
		border-radius: 35px;
		border: 1px solid #e88e1d;
		background: linear-gradient(180deg, #ffba30, #ff911e);
		box-shadow: inset 0 1px #ffd17c, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#startBtn:hover .inner {
		background: linear-gradient(180deg, #ffce44, #ffa532);
		box-shadow: inset 0 1px #ffe696, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#startBtn:active .inner {
		background: linear-gradient(180deg, #ff911e, #ffbb30);
		box-shadow: inset 0 1px #ffb050, 0 2px 3px rgba(0, 0, 0, .2);
	}

	.share {
		display: flex;
		flex-direction: row;
		justify-content: center;
	}

	#shareApp {
		width: 80px;
		height: 30px;
		margin: 10px;
		padding: 5px;
		border-radius: 40px;
		background: rgba(0, 0, 0, .1);
		box-shadow: inset 0 2px 3px rgba(0, 0, 0, .07), 0 1px hsla(0, 0%, 100%, .5);
	}


	#shareApp .inner {
		width: 100%;
		height: 100%;
		line-height: 20px;
		color: #fff;
		font-size: 12px;
		text-align: center;
		text-shadow: 0 1px 2px rgba(0, 0, 0, .3);
		border-radius: 35px;
		border: 1px solid #97d110;
		background: linear-gradient(180deg, #19ac18, #19ac18);
		box-shadow: inset 0 1px #97d110, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#shareApp:hover .inner {
		background: linear-gradient(180deg, #137e11, #137e11);
		box-shadow: inset 0 1px #97d110, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#shareApp:active .inner {
		background: linear-gradient(180deg, #19ac18, #19ac18);
		box-shadow: inset 0 1px #97d110, 0 2px 3px rgba(0, 0, 0, .2);
	}


	#luckyMoney {
		width: 80px;
		height: 30px;
		margin: 10px;
		padding: 5px;
		border-radius: 40px;
		background: rgba(0, 0, 0, .1);
		box-shadow: inset 0 2px 3px rgba(0, 0, 0, .07), 0 1px hsla(0, 0%, 100%, .5);
	}


	#luckyMoney .inner {
		width: 100%;
		height: 100%;
		line-height: 20px;
		color: #fff;
		font-size: 12px;
		text-align: center;
		text-shadow: 0 1px 2px rgba(0, 0, 0, .3);
		border-radius: 35px;
		border: 1px solid #e88e1d;
		background: linear-gradient(180deg, #f0713f, #f0713f);
		box-shadow: inset 0 1px #ffd17c, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#luckyMoney:hover .inner {
		background: linear-gradient(180deg, #c78f41, #c78f41);
		box-shadow: inset 0 1px #ffe696, 0 2px 3px rgba(0, 0, 0, .2);
	}

	#luckyMoney:active .inner {
		background: linear-gradient(180deg, #f0713f, #f0713f);
		box-shadow: inset 0 1px #ffb050, 0 2px 3px rgba(0, 0, 0, .2);
	}


	#tempContainer {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
		z-index: -1;
	}

	.tempItem {
		position: absolute;
		white-space: nowrap;
		color: #777;
		animation: flash 1.6s ease-out both;
	}

	@-webkit-keyframes flash {
		0% {
			opacity: 0;
			transform: translate3d(-50%, -50%, 0) scale(1.5);
			color: transparent;
			text-shadow: 0 0 5px rgba(0, 0, 0, .5);
		}

		50% {
			opacity: 1;
		}

		to {
			opacity: 0;
			transform: translate3d(-50%, -50%, 0) scale(.5);
		}
	}

	@keyframes flash {
		0% {
			opacity: 0;
			transform: translate3d(-50%, -50%, 0) scale(1.5);
			color: transparent;
			text-shadow: 0 0 5px rgba(0, 0, 0, .5);
		}

		50% {
			opacity: 1;
		}

		to {
			opacity: 0;
			transform: translate3d(-50%, -50%, 0) scale(.5);
		}
	}

	#footer {
		position: absolute;
		bottom: 70px;
		left: 0;
		width: 100%;
		transition: .3s;
	}

	#footer.hide {
		transform: translateY(44px);
		opacity: 0;
	}

	#toggle {
		position: absolute;
		bottom: 9px;
		left: 50%;
		transform: translateX(-50%);
		border-radius: 20px;
		background: hsla(0, 0%, 100%, .6);
		padding: 2px;
		font-size: 12px;
	}

	#toggle .option {
		display: inline-block;
		color: #999;
		line-height: 1;
		padding: 5px 10px;
		transition: .3s;
	}

	#toggle .option.selected {
		color: #fff;
	}

	#toggle .hb {
		box-sizing: content-box;
		content: "";
		position: absolute;
		top: 2px;
		left: 2px;
		width: 4em;
		height: 1em;
		border-radius: 20px;
		background: #00bdd6;
		padding: 5px 10px;
		transition: .3s;
		z-index: -1;
	}

	#toggle .hb.monster {
		left: 70px;
		width: 5em;
		background-color: #e80773;
	}

	.fab {
		position: absolute;
		bottom: 0;
		right: 10px;
		width: 44px;
		height: 44px;
		border-radius: 50%;
		background: rgba(0, 0, 0, .5) no-repeat 50%/24px auto;
	}

	#getRestaurants {
		background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' width='512' height='512'%3E%3Cpath d='M256 0C156.748 0 76 80.748 76 180c0 33.534 9.289 66.26 26.869 94.652l142.885 230.257A15 15 0 0 0 258.499 512h.119a14.997 14.997 0 0 0 12.75-7.292L410.611 272.22C427.221 244.428 436 212.539 436 180 436 80.748 355.252 0 256 0zm128.866 256.818L258.272 468.186l-129.905-209.34C113.734 235.214 105.8 207.95 105.8 180c0-82.71 67.49-150.2 150.2-150.2S406.1 97.29 406.1 180c0 27.121-7.411 53.688-21.234 76.818z' fill='%23FFF'/%3E%3Cpath d='M256 90c-49.626 0-90 40.374-90 90 0 49.309 39.717 90 90 90 50.903 0 90-41.233 90-90 0-49.626-40.374-90-90-90zm0 150.2c-33.257 0-60.2-27.033-60.2-60.2 0-33.084 27.116-60.2 60.2-60.2s60.1 27.116 60.1 60.2c0 32.683-26.316 60.2-60.1 60.2z' fill='%23FFF'/%3E%3C/svg%3E");
	}

	#editMenu {
		bottom: 54px;
		background-size: 20px auto;
		background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 317.825 317.825' width='512' height='512'%3E%3Cg fill='%23FFF'%3E%3Cpath d='M301.934 143.021H15.891C7.119 143.021 0 150.14 0 158.912s7.119 15.891 15.891 15.891h286.042c8.74 0 15.891-7.119 15.891-15.891.001-8.772-7.15-15.891-15.89-15.891zM15.891 79.456h286.042c8.74 0 15.891-7.119 15.891-15.891s-7.151-15.891-15.891-15.891H15.891C7.119 47.674 0 54.793 0 63.565s7.119 15.891 15.891 15.891zM301.934 238.369H15.891C7.119 238.369 0 245.52 0 254.26s7.119 15.891 15.891 15.891h286.042c8.74 0 15.891-7.151 15.891-15.891.001-8.74-7.15-15.891-15.89-15.891z'/%3E%3C/g%3E%3C/svg%3E");
	}

	#menuModal {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, .3);
	}

	#menuModal form {
		position: absolute;
		top: 10px;
		left: 10px;
		right: 10px;
		padding: 0 10px;
		background-image: linear-gradient(180deg, #5d4e48, #372d27);
		border: 1px solid #22201f;
		border-radius: 7px;
		box-shadow: inset 0 1px 0 hsla(0, 0%, 100%, .3), 0 2px 10px rgba(0, 0, 0, .3);
	}

	#menuModal .title {
		display: block;
		text-align: center;
		font-size: 32px;
		color: #fff;
		margin: 20px 0;
		text-shadow: 0 -2px rgba(0, 0, 0, .7);
	}

	#menuModal textarea {
		width: 100%;
		height: 13em;
		background: #fff;
		border: 1px solid #22201f;
		border-radius: 7px;
		padding: 7px 10px;
		margin-bottom: 10px;
		line-height: 1.5;
	}

	#menuModal button {
		width: 100%;
		font-size: 16px;
		color: #fff;
		text-shadow: 0 1px rgba(0, 0, 0, .3);
		background: #f6b43d;
		border-radius: 7px;
		margin-bottom: 10px;
	}
</style>
