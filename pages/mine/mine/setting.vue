<template>
	<view class="set_box">
		<view class="fengexian"></view>
		<view class="text_setting">
			用户协议
		</view>
		<view class="fengexian"></view>
		<view class="text_setting">
			权限管理
		</view>
		<view class="fengexian"></view>
		<view class="text_setting">
			开关设置
		</view>
		<view class="fengexian"></view>
		<view class="text_setting">
			隐私
		</view>
		<view class="fengexian"></view>
		<view class="text_setting">
			版本更新
		</view>
		<view class="fengexian"></view>
		<view class="text_setting">
			更换手机号
		</view>
		<view class="fengexian"></view>
		<view class="zhuxiao" @click="zhuxiao_func(status)">
			注销账号
		</view>
		<view class="zhuxiao" @click="quit_func()">
			退出账号
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				status:'未登录'
			}
		},
		methods: {
			zhuxiao_func(a){
				uni.showModal({
					 title: '提示',
					    content: '注销成功',
					    success: function (res) {
					        if (res.confirm) {
					            console.log('用户点击确定');
								uni.setStorage({
									key:'login_success',
									data:a,
									success: function () {
									    console.log('success');
									}								
								});
								uni.navigateBack({
									
								})
					        } else if (res.cancel) {
					            console.log('用户点击取消');
					        }
					    }
				});
			},
			quit_func(){
				uni.showModal({
					 title: '提示',
					    content: '退出成功',
					    success: function (res) {
					        if (res.confirm) {
					            console.log('用户点击确定');
					        } else if (res.cancel) {
					            console.log('用户点击取消');
					        }
					    }
				});
			}
		}
	}
</script>

<style>
	.set_box{
		padding: 5px 10px;
	}
	.text_setting{
		margin: 7px;
		font-size: 15px;
		height: 30px;
		line-height: 30px;
	}
	.fengexian{
		  position: relative;
		    margin: 0 auto;
		    width: auto;
		    height: 1px;
		    background-color: #d4d4d4;
		    text-align: center;
		    font-size: 16px;
		    color: rgba(101, 101, 101, 1);
		
	}
	.zhuxiao{
		margin-top: 25px;
		background-color: #9e9e9e;
		text-align: center;
		height: 30px;
		font-size: 15px;
		line-height: 30px;
	}
	
</style>
