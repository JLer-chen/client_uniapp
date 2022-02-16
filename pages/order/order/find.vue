<template>
	<view>
		<view class="contenting">
			 <view class='home'>
			 	<swiper
			 	indicator-dots 	
			 	circular
			 	autoplay
			 	interval=3000
			 	>
			 		<swiper-item v-for="(item,index) in swipers" :key="index" @click="get_new(index)">
			 			<image :src="item" @click="get_new(index)"></image>
			 		</swiper-item>
			 		<swiper-item>
						<image src="../../../static/hr.png" @click="get_news1()"></image>
					</swiper-item>
					<swiper-item>
						<image src="../../../static/jiankong_img2.png"></image>
					</swiper-item>
			 	</swiper>
			 </view>
			<view class="contenting2">
				<view class="text">精彩资讯</view>
				<view class="part_1" @click="drink_func()" >
					<image src="../../../static/drink.png" class="image_1" ></image>
					
					<text class=: block>适当饮酒真的能保护心血管吗？</text>
					<text class="text_small_1"></text>
				</view>
				
				<view class="part_2"  @click="chunkun_func()">
					<image src="../../../static/chunkun.png" class="image_1"></image>
					
					<text class=: block>春困是睡眠不足吗？</text>
					<text class="text_small_1"></text>
				</view>
				
				<view class="part_3">
						<image src="../../../static/touteng.png" class="image_1"></image>
					
					<text class=: block>睡觉醒来时头疼，怎么回事？</text>
					<text class="text_small_1"></text>
				</view>
				<view class="part_1">
					
				</view>
				<view class="part_4">
						<image src="../../../static/xintiao.png" class="image_1"></image>
					<text class=: block>心跳和健康的关系</text>
					<text class="text_small_1"></text>
				</view>
			</view>				
		</view>
		
	</view>
	
	
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				swipers:[]
			}
		},
		methods: {
			get_new(index){
				console.log('index is '+index);
				var s=0;
				s=index;
				console.log('s is '+s);  
				if(s==0){
					uni.navigateTo({
						url:'/pages/order/order/new0'
					})
				}
				if(s==1){
					uni.navigateTo({
						url:'/pages/order/order/new1'
					})
				}
				if(s==2){
					uni.navigateTo({
						url:'/pages/order/order/new2'
					})
				}
				if(s==3){
					uni.navigateTo({
						url:'/pages/order/order/new3'
					})
				}
				
			},
			get_news1(){
				uni.navigateTo({
					url:'/pages/order/order/new1'
				})
			},
			drink_func(){
				uni.navigateTo({
					url:'/pages/order/order/drink_vue'
				})
			},
				
			chunkun_func(){
				uni.navigateTo({
					url:'/pages/order/order/chunkun_vue'
				})
			}
		},
		onLoad() {
			//模拟ajax获取数据，uni.request({...});注意回调的this指向
			this.swipers=['https://app-file.beitaichufang.com/img/H5/web/banner/banner20.jpg',
			"https://app-file.beitaichufang.com/img/H5/web/banner/banner21.jpg",
			"https://app-file.beitaichufang.com/img/H5/web/banner/banner22.jpg",
			"https://app-file.beitaichufang.com/img/H5/web/banner/banner23.jpg"
			];
			
		}
	}
</script>

<style scoped lang="scss">
	.contenting{
			margin: 10upx 15upx;
			width: 100%;
			}
	.uni-bg-red{
			border-radius: 30rpx;
			}
	
	.swiper{
			
			width: 100%;
		}
	.contenting2{
		margin: 50upx 15upx;
	}
	.text{
		font-size: larger;
		font-weight: 500;
	}
	.part_1{
		margin-top: 15upx;
		/*float: left;*/
		display: inline-block;
	}
	.part_2{
		margin-top: 15upx;
		/*float: left;*/
		display: inline-block;
	}
	.part_3{
		margin-top: 15upx;
		/*float: left;*/
		display: inline-block;
	}
	.part_4{
		margin-top: 15upx;
		/*float: left;*/
		display: inline-block;
	}
	.image_1{
		width: 150px;
		height: 90px;
		float: left;
		margin: 10px 10px;
		border-radius: 50%;
	}
	.text_1{
		margin: 5px 5px;
		float: right;
	}
	.home{
		swiper{
			width: 90%;
			text-align: center;
			position: relative;left: 10px;
		}
		image{
			width:100%;
			height: 100%;
		}
	}
</style>
