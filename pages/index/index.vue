<template>
	<view class="content">
		<view class="header">
			<view class="header_fake"></view>
			<view class="header_text">
				微信
			</view>
			<view class="header_icon">
				<iconfont name="icon-add"></iconfont>
			</view>
		</view>
		<view class="search">
			<uni-search-bar placeholder="搜索" bgColor="#fff" @confirm="search" />
		</view>
		<view class="mail">
			<view class="item" v-for="item,index in mailList" :key="item.id">
				<uni-swipe-action-item :right-options="options" @click="onClick($event,index)" :show=isOpen>
					<view class="item_body">
						<view class="img">
							<image src="../../static/morentouxiang.jpg" mode=""></image>
						</view>
						<free-badge>1</free-badge>
						<view class="mail-content">
							<view class="left">
								<view class="name">{{item.name}}</view>
								<view class="name_s">{{item.lastInfo.name}}:{{item.lastInfo.content}}</view>
							</view>
							<view class="right">
								<view class="time">{{item.createTime}}</view>
								<view class="fake"></view>
							</view>
						</view>
					</view>
				</uni-swipe-action-item>
			</view>
		</view>
	</view>
</template>

<script>
	import freeBadge from '@/components/free-badge/index.vue'
	export default {
		components:{
			freeBadge
		},
		data() {
			return {
				title: 'Hello',
				mailList: [{
						id: 1,
						name: '天牛大队',
						img: '111',
						lastInfo: {
							name: 'ckj',
							content: '交作业了1'
						},
						createTime: '23:16'
					},
					{
						id: 2,
						name: '天牛大队',
						img: '111',
						lastInfo: {
							name: 'ckj',
							content: '交作业了2'
						},
						createTime: '23:16'
					},
					{
						id: 3,
						name: '天牛大队',
						img: '111',
						lastInfo: {
							name: 'ckj',
							content: '交作业了3'
						},
						createTime: '23:16'
					},
				],
				options: [{
					text: '标为已读',
					style: {
						backgroundColor: '#1d7efe',
						marginLeft: '10'
					}
				}, {
					text: '不显示',
					style: {
						backgroundColor: '#ffbe5b'
					}
				}, {
					text: '删除',
					style: {
						backgroundColor: '#dd524d'
					}
				}],
				autoClose: false,
				isOpen: 'none'
			}
		},
		onLoad() {

		},
		methods: {
			search() {

			},
			cancelInfo(title, index) {
				uni.showModal({
					title: '提示',
					content: title,
					success: res => {
						if (res.confirm) {
							this.mailList.splice(index, 1)
						}
					}
				});
			},
			onClick(e, index) {
				console.log(e.content.text, index);
				switch (e.content.text) {
					case '标为已读':
						break
					case '不显示':
						this.cancelInfo('不显示该聊天', index)
						break
					case '删除':
						this.cancelInfo('删除该聊天', index)
						break
				}
			},

		},
	}
</script>

<style lang="scss" scoped>
	/deep/ .uni-swipe_box {
		height: 128rpx;
	}

	/deep/ .uni-swipe {
		width: 100%;
	}

	/deep/ .uni-swipe_button-group {
		width: 400rpx;

		span {
			font-size: 14px;
			letter-spacing: 1rpx;
		}
	}

	.content {
		width: 100%;
		height: auto;
		min-height: calc(100vh - 50px);
		background-color: #ededed;

		.header {
			box-sizing: border-box;
			width: 100%;
			height: 100rpx;
			display: flex;
			justify-content: space-between;
			line-height: 100rpx;
			padding: 0 18rpx;

			.header_text {
				color: #000;
				font-weight: bold;
			}

			.header_fake {
				visibility: hidden;
			}

			.header_icon {
				font-size: 20px;
			}
		}

		.mail {
			width: 100%;
			// padding: 20rpx 0;

			.item {
				width: 100%;
				box-sizing: border-box;
				display: flex;
				justify-content: space-between;
			}
		}
	}

	.item_body {
		display: flex;
		padding: 20rpx;

		.img {
			width: 100rpx;
			height: 100rpx;

			image {
				width: 100%;
				height: 100rpx;
				border-radius: 20rpx;
			}
		}

		

		.mail-content {
			flex: 1;
			display: flex;
			justify-content: space-between;
			margin-left: 20rpx;
			padding: 10rpx 0;
			border-bottom: 1px solid #e5e5e5;

			.left {
				.name_s {
					margin-top: 10rpx;
					font-size: 14px;
					color: #b8b8b8;
				}
			}

			.right {
				margin-right: 16rpx;
				font-size: 10px;
				color: #b8b8b8;
				display: flex;
				flex-direction: column;
				justify-content: space-between;

				.time {
					align-items: center;
					line-height: 16px;
				}
			}
		}
	}
</style>
