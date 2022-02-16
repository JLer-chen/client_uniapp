<template>
	<view class="changinfo">
		<view class="box">
			<view class="img-box">
				<image class="img" :src='src' @click="chooseimg()" ></image>
				<view class="text">
					点击更换头像
				</view>
			</view>
		</view>
		<view class="info-box">
			<view class="text-box">
				<view class="left">
					昵称
				</view>
				<navigator url="nicheng" class="right">
					{{name}}
				</navigator>
				
			</view>
			<view class="text-box">
				<view class="left">
					电话
				</view>
				
				<view class="right">
					131735
				</view>
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src:"../../../static/find.png",
				name:'张三'
			}
		},
		methods: {
			chooseimg(){
				uni.chooseImage({
					count:1,
					sourceType:['album'],
					sizeType:['orginal','compressed'],
					success: (res) => {
						console.log(res.tempFilePaths);
						this.src=res.tempFilePaths;
					}
					
					
				})
			}
		},
		onShow:function(){
			uni.getStorage({
				key:'nicheng_baocun',
				success: (res)=> {
				    console.log(res.data);
					this.name=res.data;
					console.log(this.name);
				}
			})
		}
	}
</script>

<style>
	
	
	
	.box{
		width: 100%;
		height: 150px;
		margin: 0 auto;
		border-top: 1px solid #333333;
		border-bottom: 1px solid #333333;
	}
	.img-box{
		text-align: center;
	}
	.img{
		margin: 15px;
		width: 70px;
		height: 70px;
		border-radius: 50%;
	}
	.text{
		font-size: 13px;
		 margin-top: 10px;
		 color: #999999;
	}
	.info-box{
		padding: 0 10px;
	}
	.text-box{
		width: 100%;
		height: 40px;
		line-height: 40px;
		
	}
	.icon-box{
		float: right;
		height: 10px;
		width: 10px;
		
	}
	.right{
		float: right;
		font-size: 15px;
		margin-right: 7px;
		color: #999999;
		
	}
	.left{
		float: left;
		font-weight: 200;
		font-size: 15px;
		
	}
</style>
