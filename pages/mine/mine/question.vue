<template>
	<view>
		<image src="../../../static/question_1.png" class="question_icon"></image>
		<view class="question_text">
			<navigator url="zanting">
				什么是睡眠呼吸暂停
			</navigator>
		</view>
		<view class="fengexian_question"></view>
		<view class="question_text">
			<navigator url="rqun">
				睡眠呼吸暂停常发生人群
			</navigator>
		</view>
		<view class="fengexian"></view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.question_text{
		margin: 10px 10px;
		font-size: 20px;
	}
	.fengexian_question{
		  position: relative;
		    margin: 0 auto;
		    width: auto;
		    height: 1px;
		    background-color: #d4d4d4;
		    text-align: center;
		    font-size: 16px;
		    color: rgba(101, 101, 101, 1);
		
	}
	.question_icon{
		height: 30px;
		width: 30px;
		margin: 5px 5px;
	}
</style>
