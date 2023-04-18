<template>
	<view class='radius' :style="'width:'+width+'rpx;height:'+height+'rpx;right:'+right+'rpx;top:'+top+'rpx'"
	>
	{{Data}}
	</view>
</template>

<script>
	export default {
		props:{
			Data:{
				type:Number,
				default:0
			},
			badgeClass:{
				type:String,
				default:""
			},
			badgeStyle:{
				type:String,
				default:""
			},
			width: { 
				type: Number,
				default () {
					return 40
				}
			},
			height: { 
				type: Number,
				default () {
					return 40
				}
			},
			right: {
				type: Number,
				default () {
					return 24
				}
			},
			top: {
				type: Number,
				default () {
					return -10
				}
			}
		},
		data() {
			return {
				
			};
		},
		
	}
</script>

<style lang="scss">
.radius {
			color: white;
			position: relative;
			line-height: 40rpx;
			text-align: center;
			border-radius: 50%;
			font-size: 14px;
			background-color: #ff4341;
		}
</style>
