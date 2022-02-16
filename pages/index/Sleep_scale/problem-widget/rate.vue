<template>
	<view class="pages-rate">
		<view class="title">
			<view class="title-left">
				<image class="title-img" src="/static/common/problem.png" mode=""></image>
				<view class="title-progress">已完成{{percent}}%</view>
			</view>
			<!-- <view class="title-right">额度近在眼前</view> -->
		</view>
		<progress :percent="percent" active active-mode="forwards" stroke-width="3" activeColor="#458FFF" backgroundColor="#E5E5E5" border-radius="50%" />
	</view>
</template>

<script>
	export default {
		props: {
			percent: {
				default: 30
			}
		}
	}
</script>

<style lang="scss" scoped>
	.pages-rate {
		width: 750rpx;
		height: 100rpx;
		padding: 0 30rpx;
		box-sizing: border-box;
		margin-top: 30rpx;
		.title {
			display: flex;
			align-items: center;
			justify-content: space-between;
			height: 80rpx;
			&-left {
				display: flex;
				align-items: center;
			}
			&-img {
				width: 40rpx;
				height: 40rpx;
			}
			&-progress {
				margin-left: 10rpx;
				font-size: 28rpx;
				color: #0A58F6;
			}
			&-right {
				font-size: 28rpx;
				color: #0A58F6;
			}
		}
	}
</style>
