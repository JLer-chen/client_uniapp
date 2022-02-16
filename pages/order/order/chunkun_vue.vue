<template>
	<view class="chunkun">
		<view class="title_chu">
			春困是睡眠不足吗？
		</view>
		<view class="fengexian_question"></view>
		<view class="box_chu">
			<image src="../../../static/chunkun_img.png" class="chunkun_img"></image>
			<view class="text_chun">
				春困的几种解决方法
			</view>
			<view class="text_sec">
				1、从晨跑开始.
				　　晨跑可以激活新陈代谢，刺激全身的血液循环，将氧气和葡萄糖输送到大脑，令你一整天都保持着充沛精力。如果能长期坚持，你的代谢状态越来越好，整个人的状态都会因此焕然一新呢！
				
				　　推荐：如果你之前没有做过跑步训练，可以这样开始练习：将3分钟的跑步和3分钟的快走交替进行，持续18分钟。一周之后，逐渐减少快走的时间，增加跑步的总时间，这样在一个月之内将18分钟全部转换为跑步，之后再逐渐增加跑步的总时长。
			</view>
			<view class="fengexian_question"></view>
			<view class="text_sec">
				2、充分地呼吸
				
				　　在工作学习的间隙，不妨做个深呼吸，将力量集中在你腹部，让新鲜空气从鼻腔开始进入并充满你的整个肺部，再简单不过的动作，却能有效地帮你注入更多的能量，你的脑部细胞在获得了充分的氧气后，亦能更清晰地思考。
				
				　　推荐：找一个能呼吸到新鲜空气的所在，用鼻子深吸一口气，默数3，然后再用鼻子呼出，默数6后结束，反复练习10次。
			</view>
			<view class="fengexian_question"></view>
			<view class="text_sec">
				3、补充蛋白质
				
				　　进入温暖春季，又是一年“减肥时”，但是爱美的你也得保证每天15-25克蛋白质的摄入量哦！（相当于3个中等大小的鸡蛋和一大块鸡胸肉中所含的蛋白质）足够的蛋白质有助于保持你体内的血糖稳定，防止午后体内血糖过低而出现犯困症状。
				
				　　推荐：不要一顿将这么多蛋白质全部摄入，建议均匀分配到早餐和午餐中。
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
	.chunkun{
		padding: 0 10px;
	}
	.title_chu{
		font-size: 30px;
		margin: 5px 5px;
	}
	.chunkun_img{
		height: 300px;
	}
	.box_chu{
		margin: 5px 10px;
		
		text-align: center;
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
	.text_chun{
		margin: 5px 5px;
		font-size: 15px;
	}
	.text_sec{
		margin: 5px 5px;
	}
</style>
