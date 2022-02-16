<template>
	<view>
		<view class="mine_part1">
			<image class="touxiang" v-show="un_alive" src="../../../static/person.png" mode="" @click="get_login()"></image>
			<image class="touxiang" v-show="alive" src="../../../static/usr_alive.png" mode="" @click="get_login()"></image>
			<!-- <input v-model="usr_name" type="text " maxlength="11" class="usr_name" /> -->
			<view class="usr_name">{{usr_name}}</view>
		</view>
		<view class="mine_part2">
			<view class="fengexian"></view>
			<view class="chuizhijuzhong" @click="get_info()">
				<image class="mine_info" src="../../../static/information.png"  ></image>
				<text>个人信息</text>
				
			</view>
			<view class="fengexian"></view>
			<view class="chuizhijuzhong" @click="set_tel()">
				<image class="mine_tel" src="../../../static/tel.png" ></image>
				<v-layout align-center justify-center fill-height >紧急联系人</v-layout>
			</view>
			<view class="fengexian"></view>
			<view class="chuizhijuzhong" @click="get_question()">
				<image class="mine_question" src="../../../static/question.png" ></image>
				<v-layout align-center justify-center fill-height >常见问题</v-layout>
			</view>
			<view class="fengexian"></view>
			<view class="chuizhijuzhong" @click="get_setting()">
				<image class="mine_setting" src="../../../static/setting.png" ></image>
				<v-layout align-center justify-center fill-height >设置</v-layout>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				usr_name:"未登录",
				alive:false,
				un_alive:true
			}
		},
		methods: {
			get_info(){
				uni.navigateTo({
					url:'/pages/mine/mine/info'
				})
			},
			set_tel(){
				uni.navigateTo({
					url:'/pages/mine/mine/tel'
				})
			},
			get_question(){
				uni.navigateTo({
					url:'/pages/mine/mine/question'
				})
			},
			get_setting(){
				uni.navigateTo({
					url:'/pages/mine/mine/setting'
				})
			},
			get_login(){
				uni.navigateTo({
					url:'/pages/mine/mine/login'
				})
			}
		},
		onShow: function() {
			
			uni.getStorage({
				key: 'login_success',
				    success: (res)=> {
				        console.log(res.data);
						this.usr_name=res.data;
						console.log(this.usr_name);
						if(this.usr_name!='未登录'){
							this.alive=true;
							this.un_alive=false;
							console.log('a is '+this.alive+' un_a is '+this.un_alive);
						
							uni.setStorageSync('is_login',true);
							
							}
							else{
								this.alive=false;
								this.un_alive=true;
								console.log('a is '+this.alive+' un_a is '+this.un_alive);
								uni.setStorageSync('is_login',false);
							}
				    }
			});
			
		
	},
	}
</script>

<style scoped>
	.usr_name{
		font-size: 20px;
		color: #8a8a8a;
		position: relative;left: 20px;
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
		.mine_part1{
			height: 125px;
			width: auto;
			background-color: #4CD964;
			
		}
			
		.mine_part2{
			margin: 20px 15px;
		}
		.touxiang{
			margin: 15px 20px;
			width: 50px;
			height: 50px;
		}
			
		.chuizhijuzhong {
			margin-top: 15px;
			margin-bottom: 15px;
		}	
		.tel{
			margin-bottom: 15px;
		}
		.question{
			margin-bottom: 15px;
			
		}
		.setting{
			margin-bottom: 15px;
			
		}
		.mine_info{
			width:20px;
			height:15px
			
		}
		.mine_tel{
			width:20px;
			height:15px
		}
		.mine_question{
			width:20px;
			height:15px
		}
		.mine_setting{
			width:20px;
			height:15px
		}
</style>
