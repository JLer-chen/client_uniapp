<template>
	<view class="drink_box">
		<view class="title_drink">
		适当饮酒真的能保护心血管吗？
		</view>
		<view class="fengexian_question"></view>
		<view class="drink_box1">
			<image src="../../../static/yinjiu.png" class="drink_img"></image>
			<view class="fengexian_question"></view>
			<view class="title_sec">
				常见的关于酒对人体健康影响的知识
			</view>
			<view class="drink_text">
				“酒精中的主要成分是乙醇，乙醇进入人体之后，有可能会对胃黏膜造成刺激，尤其是本身就有基础胃病的人群，长时间经受酒精刺激后，可能会引发胃病，导致胃溃疡甚至胃癌。另外，喝酒之后酒精中的乙醇主要通过肝脏代谢，长时间喝酒会加重肝脏负担，尤其是本身有肝病的人群。如果长期喝酒会引起酒精性肝病，甚至引起酒精性肝硬化，最终导致肝癌的发生。少量喝酒可以起到活血化瘀、改善循环作用，但过量喝酒有害健康。尤其是有基础胃病、肝病的人群，必须在医生的指导下饮酒。
			</view>
			<view class="fengexian_question"></view>
			<view class="drink_text">
				二、损害肝脏
				
				在喝酒之后，酒精都需要通过肝脏代谢出体外。但是人体肝脏的解酒能力是有限的，适量摄入酒精不会对肝脏造成任何损伤。但是一个人若长时间饮酒，大量酒精在体内堆积，就会给肝脏造成极大负担，从而损害肝脏正常功能，轻者导致酒精肝，重者还可能引发严重肝病。
			</view>
			<view class="fengexian_question"></view>
			<view class="drink_text">
				三、危害肠胃
				
				人体胃黏膜是十分脆弱的，大量酒精的摄入会损害胃黏膜，从而出现反酸、胀气等一系列反应。而如果本身胃部就有疾病，则会使病情更加严重。很多人在大量饮酒后会出现呕吐的情况，这主要就是因为饮酒过多，造成胃部负担过重而引发的。
			</view>
			<view class="fengexian_question"></view>
		</view>
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
	.title_drink{
		font-size: 25px;
		margin: 5px 5px;
	}
	.drink_box{
		padding: 0 10px;
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
	.drink_box1{
		margin: 5px 10px;
		
		text-align: center;
	}
	.title_sec{
		margin: 5px 5px;
		font-size: 15px;
	}
	.drink_text{
		margin: 5px 5px;
	}
	.drink_img{
		height: 200px;
	}
</style>
