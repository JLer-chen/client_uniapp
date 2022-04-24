<template>
	<view class="pages-msg">
		<view class="title">匹兹堡睡眠量表与睡眠检测综合得出结果</view>
		<!-- <view class="title" v-if="problemModel.rule == 0">您的情况无法智能推荐，稍后有专 人为您服务，请留意接听电话</view> -->
		<view class="success">
			<image class="img" src="/static/success.png" mode=""></image>
		</view>
		
		<!-- <view class="complete conn" v-if="problemModel.rule == 0" @click="back()">完成</view> -->
		<view class="recommend conn" @click="check_res()">点击查看</view>
		<!-- <view class="tips" v-if="problemModel.rule == 0">{{count}}s后返回</view> -->
	</view>
</template>

<script>
	var timer = null
	export default {
		data() {
			return {
				count: 5,
				problemModel: null,
				psqi: 0
			}
		},
		methods:{
			check_res(){
				console.log('123');
				uni.showLoading({
				    title: '加载中'
				});
				uni.request({
					url:'http://192.168.137.146:8088/testlocal',
					method:'GET',
					success: (res) => {
						console.log(res.data);
						var seg=new Array();
						for(var i=0;i<8;++i){
							if(i==0){
								seg[i]=res.data.sol;
							}
							if(i==1){
								seg[i]=res.data.sol_sc;
							}
							if(i==2){
								seg[i]=res.data.eff;
							}
							if(i==3){
								seg[i]=res.data.eff_sc;
							}
							if(i==4){
								seg[i]=res.data.tst;
							}
							if(i==5){
								seg[i]=res.data.tst_sc;
							}
							if(i==6){
								seg[i]=res.data.waso;
							}
							if(i==7){
								seg[i]=res.data.waso_sc;
							}	
						}
						uni.setStorageSync('seg_settle',seg);
						uni.hideLoading()
						uni.navigateTo({
							url:"/pages/index/Sleep_scale/problem-widget/show",
							
						})
					}
				})
			
			}
		}
	
	}
</script>

<style lang="scss" scoped>
	.pages-msg {
		width: 750rpx;
		padding: 0 40rpx;
		box-sizing: border-box;
		.title {
			font-size: 38rpx;
			color: #222;
			font-weight: bold;
		}
		.success {
			margin: 100rpx auto;
			width: 300rpx;
			height: 300rpx;
		}
		.img {
			width: 300rpx;
			height: 300rpx;
		}
		.conn {
			margin: 0 auto;
			width: 600rpx;
			height: 88rpx;
			border-radius: 60rpx;
			text-align: center;
			line-height: 88rpx;
			font-size: 32rpx;
			color: #222;
			font-weight: bold;
		}
		.complete {
			border: 1rpx solid #CCCCCC;
		}
		.recommend {
			background-color: #0A58F6;
			color: #FFFFFF;
		}
		.tips {
			height: 70rpx;
			line-height: 70rpx;
			font-size: 28rpx;
			color: #868686;
			text-align: center;
		}
	}
</style>
