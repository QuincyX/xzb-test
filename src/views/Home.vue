<template lang="pug">
.page
  .siderBar
    .logo 商城管理中心
    .list
      .item(v-for="(i,n) in siderNavList" :key="n")
        .title(@click="handleJumpLink(i,n)") {{i.title}}
        .subList(v-if="i.hasChild" v-show="currentNavIndex===n")
          .subItem(v-for="(j,m) in i.children" :key="m")
            .title(@click="$router.push(j.link)") {{j.subTitle}}

  .pageContent
    .headerBar
      .leftBtn 折叠
      .item 消息
      .item 日志
      .item.userInfo
        .userFace
          img
        .userName 用户名
    .leftContent
      el-card.card(header="店铺营业额")
        .cardList
          .item(v-for="(i,n) in card1" :key="n")
            .label {{i.label}}
            .value {{i.value}}
      .fian.card
        .title 我的白条
        .content
          .item
            .label 白条额度：
            .value 280,000
          .item
            .label 还款额度：
            .value 280,000
          .item
            .label 今日待还：
            .value 280,000
      el-card.card(header="订单")
        .cardList
          .item(v-for="(i,n) in card2" :key="n")
            .label {{i.label}}
            .value {{i.value}}
      el-card.card(header="经营攻略")
        .topicList
          .item
            .title 了解信用额度
            .desc 宝专属信用额度
            .btn 前去了解
          .item
            .title 了解信用额度
            .desc 宝专属信用额度
            .btn 前去了解
    .rightContent
      .fian.fian1.card
        .title 商户信息
        .content
          .item
            .label 尚湖等级：
            .value 1
          .item
            .label 注册年限：
            .value 0
          .item
            .label 商铺类型：
            .value 精英店
          .item
            .label 经营地址：
            .value(style="color:#fff;font-weight:normal;font-size:1em;") blablablablablablablabla
      .fian.fian2.card
        .title 诚信资质
        .content
          .item
            .label 信用等级：
            .value 1
          .item
            .label 满意度：
            .value 5
          .item
            .label 厂家认证：
            .value 是
          .item
            .label 诚信商户认证：
            .value 未完成
      el-card
        .cardHeader(slot="header")
          span 宝头条
          .btn 查看全部
        .newsList
          .item(v-for="(i,n) in newsList" :key="n")
            .index {{n+1}}
            .title {{i.title}}

</template>
<script>
export default {
	data() {
		return {
			siderNavList: [
				{ title: "首页", link: "/", hasChild: false },
				{ title: "首页", link: "/", hasChild: false },
				{
					title: "商品管理1",
					hasChild: true,
					children: [
						{ subTitle: "商品分类11", link: "/" },
						{ subTitle: "商品分类12", link: "/" },
						{ subTitle: "商品分类13", link: "/" }
					]
				},
				{
					title: "商品管理2",
					hasChild: true,
					children: [
						{ subTitle: "商品分类21", link: "/" },
						{ subTitle: "商品分类22", link: "/" },
						{ subTitle: "商品分类23", link: "/" }
					]
				},
				{
					title: "商品管理3",
					hasChild: true,
					children: [
						{ subTitle: "商品分类31", link: "/" },
						{ subTitle: "商品分类32", link: "/" },
						{ subTitle: "商品分类33", link: "/" }
					]
				},
				{
					title: "商品管理4",
					hasChild: true,
					children: [
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" }
					]
				},
				{
					title: "商品管理5",
					hasChild: true,
					children: [
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" }
					]
				},
				{
					title: "商品管理6",
					hasChild: true,
					children: [
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" },
						{ subTitle: "商品分类", link: "/" }
					]
				}
			],
			currentNavIndex: -1,
			card1: [
				{ label: "总营业额", value: "2,800,000" },
				{ label: "总待入账", value: "2,800,000" },
				{ label: "退货金额", value: "2,800,000" },
				{ label: "已收货入账金额", value: "2,800,000" },
				{ label: "总营业额", value: "2,800,000" }
			],
			card2: [
				{ label: "全部订单", value: "2,800,000" },
				{ label: "已付款", value: "2,800,000" },
				{ label: "未付款", value: "2,800,000" },
				{ label: "已发货", value: "2,800,000" },
				{ label: "已到货", value: "2,800,000" }
			],
			newsList: [
				{ title: "news 111111111" },
				{ title: "news 22221e32143" },
				{ title: "news 215343425324" },
				{ title: "news 345ytherdgfv" },
				{ title: "news bsrgthu46" }
			]
		};
	},
	methods: {
		handleJumpLink(val, index) {
			if (this.currentNavIndex === index) {
				this.currentNavIndex = -1;
			} else {
				this.currentNavIndex = index;
			}
			if (!val.hasChild) {
				this.$router.push(val.link);
			}
		}
	}
};
</script>

<style lang="less" scoped>
@import url("../style/theme.less");
@import url("../style/mixin.less");

@siderBarWidth: 200px;
.page {
	.siderBar {
		position: absolute;
		left: 0;
		top: 0;
		bottom: 0;
		width: @siderBarWidth;
		background: #00152a;
		color: @white;
		.logo {
			.size(22px);
			padding: 1em;
			background: #002140;
		}
		.list {
			.item {
				.title {
					padding: 1em;
					&:after {
						content: ">";
						float: right;
					}
					&:hover {
						background: @primary;
					}
				}
				.subItem {
					background: #000c18;
				}
			}
		}
	}
	.pageContent {
		position: absolute;
		left: @siderBarWidth;
		top: 0;
		right: 0;
		bottom: 0;
		background: #f8f8f8;
		padding: 1em;
		padding-top: calc(40px + 3em);
		.headerBar {
			background: @white;
			padding: 1em;
			text-align: right;
			.border-bottom;
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			.leftBtn {
				float: left;
				margin-top: 0.5em;
			}
			.item {
				vertical-align: middle;
				display: inline-block;
				margin-right: 1em;
			}
			.userInfo {
				.userFace {
					.inline;
					.rounded(40px);
					margin-right: 1em;
					vertical-align: middle;
					background: #1890ff;
				}
				.userName {
					vertical-align: middle;
					.inline;
				}
			}
		}
		.leftContent {
			.inline;
			width: calc(100% - 400px - 1em);
			margin-right: 1em;
			.vtop;
			.cardList {
				display: flex;
				flex-wrap: wrap;
				.item {
					.hh(45px);
					width: 280px;
					.label {
						.inline;
						color: @grey;
						&:after {
							content: "：";
							display: inline;
						}
					}
					.value {
						.inline;
						.size(20px);
						font-weight: bold;
						color: @primary;
					}
				}
			}
			.topicList {
				.item {
					margin: 1em;
					padding: 1em;
					.border;
					.lh(40px);
					.inline;
					width: 300px;
					position: relative;
					.btn {
						position: absolute;
						right: 1em;
						bottom: 1em;
						color: @primary;
						padding: 5px 10px;
						line-height: 1em;
						.size(12px);
						.radius(5px);
						.border(@primary);
						&:hover {
							background: @primary;
							color: @white;
							.pointer;
						}
					}
				}
			}
		}
		.rightContent {
			.inline;
			.vtop;
			width: 400px;
			.fian1 {
				background: linear-gradient(left, #8693f3, #8693f3);
			}
			.fian2 {
				background: linear-gradient(left, #8ac3f8, #8ac3f8);
			}
			.newsList {
				.item {
					margin-bottom: 10px;
					.index {
						.inline;
						background: @primary;
						color: @white;
						.radius(3px);
						width: 20px;
						height: 20px;
						line-height: 20px;
						.center;
					}
					.title {
						.inline;
						margin-left: 1em;
					}
				}
			}
		}
	}
}
.fian {
	background: linear-gradient(left, #ff5f5f, #ffbf9c);
	.title {
		padding: 1em;
		.border-bottom;
		color: #f1fe00;
	}
	.content {
		padding: 1em;
		.item {
			.inline;
			.hh(45px);
			margin-right: 4em;
			.label {
				.inline;
				color: @white;
			}
			.value {
				.inline;
				.size(20px);
				font-weight: bold;
				color: #f1fe00;
			}
		}
	}
}
.card {
	margin-bottom: 1em;
}
.btn {
	float: right;
}
</style>
