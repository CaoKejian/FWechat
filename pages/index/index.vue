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
				<freeMediaList :item="item" :index="index" @click="gotoDetail"></freeMediaList>
			</view>
		</view>
	</view>
</template>

<script>
	import freeMediaList from '@/components/free-media-list/free-media-list.vue'
	export default {
		components: {
			freeMediaList
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
						createTime: '23:16',
						message: 2
					},
					{
						id: 2,
						name: '天牛大队',
						img: '111',
						lastInfo: {
							name: 'ckj',
							content: '交作业了2'
						},
						createTime: '23:16',
						message: 0
					},
					{
						id: 3,
						name: '天牛大队',
						img: '111',
						lastInfo: {
							name: 'ckj',
							content: '交作业了3'
						},
						createTime: '23:16',
						message: 1
					},
				],
				autoClose: false,

			}
		},
		onLoad() {

		},
		methods: {
			search() {},
			gotoDetail(e){
				uni.navigateTo({
					url:'/views/mailDetail/mailDetail?item='+ JSON.stringify(e)
				})
			}
		},
	}
</script>

<style lang="scss" scoped>


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

			.item {
				width: 100%;
				box-sizing: border-box;
				display: flex;
				justify-content: space-between;
			}
		}
	}

	
</style>
