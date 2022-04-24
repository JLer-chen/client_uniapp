<template>
	<view>
		<view>
			<view>
					<view class="inputShow">
						<image src="../../../static/mine.png" class="icon"></image>
						<text>账号</text>
						<input type="text" placeholder="请输入账号" v-model="eyetext" maxlength="11" />
						<image src="../../../static/clear.png" class="icon" @click="deletealleye()"></image>
					</view>
					<view class="inputShow">
						<image src="../../../static/pwd.png" class="icon"></image>
						<text>密码</text>
						<input type="password" placeholder="请输入密码" v-model="passtext"  />
						<image src="../../../static/clear.png" class="icon" @click="deleteallpwd()"></image>
					</view>
				</view>
				<view>
					<button class="sign" @click="sign_func(eyetext,passtext)">注册</button>
					<button class="log_in" @click="log_func(eyetext,passtext)">登入</button>
				</view>
				
				
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				eyetext:'',
				passtext:''
			}
		},
		methods: {
			deleteallpwd(){
				this.passtext=''
			}
			,
			deletealleye(){
				this.eyetext=''
			},
			log_func(a,b){
				console.log('a and b is '+a+' '+b)
				uni.request({
					url:'http://192.168.137.146:8088/post2',
					method:'POST',
					data:{
						accout_sent:a,
						password_sent:b
					},
					
					success:(res)=>{
						console.log(res);
						//console.log(res.data.)
						if(res.data.code==1){
							uni.showModal({
								 title: '提示',
								    content: '登入成功',
								    success: function (res) {
								        if (res.confirm) {
								            console.log('用户点击确定');
											uni.setStorage({
											    key: 'login_success',
											    data: a,
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
							})
						}
						else{
							uni.showModal({
								 title: '提示',
								    content: '登入失败',
								    success: function (res) {
								        if (res.confirm) {
								            console.log('用户点击确定');
										
											uni.navigateBack({
												
											})
								        } else if (res.cancel) {
								            console.log('用户点击取消');
								        }
								    }
							})
						}
					
							}
				
					
				});
				console.log("log_get");
			},
			sign_func(a,b){
				
				uni.request({
					url:'http://192.168.137.146:8088/post1',
					data:{
/* 						data:res,
						url:'baidu.com' */
						accout_sent:a,
						password_sent:b
					},
					method:'POST',
					success:(res)=>{
						console.log(res);
						uni.showModal({
							 title: '提示',
							    content: '注册成功',
							    success: function (res) {
							        if (res.confirm) {
							            console.log('用户点击确定');
							        } else if (res.cancel) {
							            console.log('用户点击取消');
							        }
							    }
						});
					}
					
				});
				console.log('sign_post');
			}
		}
	}
</script>

<style scoped>
	.inputShow{
			display: flex;
			flex-wrap: nowrap; /* 禁止自动换行*/
			padding: 5px;
			justify-content: center; /* 主轴上对齐方式*/
		}
		.inputShow text{
			margin-right: 20px;
		}
		.inputShow input{
			font-size: 14px;
		}
		.icon{
			width: 20px;
			height: 20px;
			margin-right: 10px;
		}
		.icon-clear{
			width: 20px;
			height: 20px;
		}
		.sign{
			background-color: #C0C0C0;
			width: 30%;
			height: 7%;
			
		}
		.log_in{
			background-color: #4CD964;
			width: 30%;
			height: 7%;
			
		}
</style>
