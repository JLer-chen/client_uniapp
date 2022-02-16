<template>
	<view class="modify">
		<view class="box_first">
			我的昵称
		</view>
		<input type="text" v-model="name" class="box_second"/>
		<button class="submit" @click="baocun()">保存</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name:'张三'
			}
		},
		methods: {
			baocun(){
				uni.setStorage({
					key:'nicheng_baocun',
					data:this.name,
					success: function () {
					    console.log('success');
					}
				})
				uni.navigateBack({
				
				})
			}
		}
	}
</script>

<style>
	.box_first{
		padding: 10px 15px;
		font-size: 27px;
		font-weight: 500;
	}
	.box_second{
		font-size: 20px;
		color: #999999;
		padding: 10px 15px;
		
	}
	.submit{
		
		width: 100%;
		text-align: center;
		margin-top: 50px;
		font-size: 18px;
		
	}
</style>
