<template>
	<view class="wrapper">
		<uni-easyinput ref="uipt" @confirm="goComment" suffixIcon="paperplane" v-model="replyContent"
			:placeholder="placeholder" @iconClick="goComment"></uni-easyinput>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				replyContent: "",
				placeholder: ''
			};
		},
		methods: {
			goComment() {
			
			}
		},
		onLoad(e) {
			const item = JSON.parse(e.item)
			console.log(item);
			uni.setNavigationBarTitle({
				title: item.name
			})
		}
	}
</script>

<style lang="scss">
	.wrapper {
		width: 100%;
		background: #fff;
		padding: 20rpx 30rpx;
		box-sizing: border-box;
		position: fixed;
		bottom: 0;
		left: 0;
		z-index: 100;
	}
</style>
