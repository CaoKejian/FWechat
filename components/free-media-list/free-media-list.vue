<template>
	<uni-swipe-action-item :right-options="options" @click="onClick($event,index)" :show=isOpen>
		<view class="item_body">
			<view class="img">
				<image src="../../static/morentouxiang.jpg" mode=""></image>
			</view>
			<free-badge v-if="item.message" :Data="item.message"></free-badge>
			<view class="mail-content" :style="item.message?'':'margin-left:40rpx;'">
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
</template>

<script>
	import freeBadge from '@/components/free-badge/index.vue'
	export default {
		name:"free-media-list",
		props:{
				item:Object,
				index:Number
		},
		components: {
			freeBadge
		},
		data() {
			return {
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
				isOpen: 'none'
			};
		},
		methods:{
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
		}
	}
</script>

<style lang="scss">
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
	.item_body {
		box-sizing: border-box;
		width: 100vw;
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