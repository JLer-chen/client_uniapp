<template>
	<view >
		<view class="show_data">{{year}}年{{month}}月{{day}}日</view>
		<view class="show_all">
			<view class="show_score">
				{{score}}
			</view>
			
			<view class="show_text">本次睡眠详细参数:</view>
			<view class="show_se">SE%睡眠效率：{{se}}%</view>
			<view class="show_tst">TST睡眠时长：{{tst}}min</view>
			<view class="show_sol">SOL入睡时长：{{sol}}min</view>
			<view class="show_waso">WASO醒觉时长：{{waso}}min</view>
			
			<view class="charts-box">
			  <qiun-data-charts
			    type="column"
			    :chartData="chartData"
			    background="none"
			  />
			</view>
		</view>
		
	</view>
	
</template>

<script >
	export default {
		data() {
			return {
				
				
				score:0,
				se:87,
				tst:7.5,
				sol:20,
				waso:50,
				year:2022,
				month:1,
				day:22,
				chartData:{
    "categories": [
        "SOL",
        "SE",
        "TST",
        
        "WASO",
        "PSQI"
    ],
    "series": [
        {
            "name": "分数",
            "data": [
                35,
                36,
                31,
                
                13,
				5
            ]
        }
        
    ]
}
				}
		},
		methods: {
			print_data(){
				var a=[];
				var b=[];
				uni.getStorage({
					key: 'sleep_data',
					    success: (res)=> {
					       
							a=res.data;
							// b=res.data;
							// for(var i=0;i<720;i++){
							// 	for(var j=0;j<200;j++){
							// 		a.push(b[i]);
							// 	}
							// }
							console.log(a);
							var temp_json=JSON.stringify(a);
							console.log(temp_json);
							console.log(typeof temp_json);
							uni.request({
								url:'http://192.168.137.146:8088/post3',
								method:'POST',
								data:{
									test_json:temp_json
								},
								success: (res) => {
									console.log(res.data);
									if(res.data.code==1){
										console.log('upload success');
									}
									else{
										console.log('upload fail');
									}
								}
							})
					    }
				});
			}
		},
		onShow() {
			var s=0
			uni.getStorage({
				key: 'total score',
				    success: (res)=> {
						//计算主观分数
				        console.log(res.data);
						this.score=res.data;
						s=Math.floor((100-5*res.data)/5);
						console.log(s);
						var temp_chart=this.chartData;
						temp_chart.series[0].data[4]=s;
						//this.chartData=temp_chart;
						
						//获取八个参数
						var arr=uni.getStorageSync('seg_settle');
						temp_chart.series[0].data[0]=Math.floor(arr[1]*0.8);
						temp_chart.series[0].data[1]=Math.floor(arr[3]*0.8);
						temp_chart.series[0].data[2]=Math.floor(arr[5]*0.8);
						temp_chart.series[0].data[3]=Math.floor(arr[7]*0.8);
						for(var i=0;i<5;i++){	
								this.score+=temp_chart.series[0].data[i];	
						}
						this.chartData=temp_chart;
						
						//更新数字
						this.se=Math.floor(arr[2]*100);
						this.tst=Math.floor(arr[4]);
						this.sol=Math.floor(arr[0]);
						this.waso=Math.floor(arr[6]);
						//获取日期
						var date_show=new Date();
						this.year=date_show.getFullYear();
						this.month=date_show.getMonth()+1;
						this.day=date_show.getDate();
						
						
				    }
			});
			
			
		}
	}
</script>

<style>
	.charts-box{
	  width: 100%;
	  height:300px;
	  position: absolute;top: 400px;
	}
	.show_data {
		text-indent: 25px;
		background-color: #1890FF;
		font-size: 30px;
		color: #F1F1F1;
	}
	.show_all {
		
		margin: 10px 10px;
	}
	.show_score {
		border-radius: 50%;
		border-color: #1CBBB4;
		
		width: 200px;
		height: 200px;
		border: #1890FF solid 2px;
				position: absolute; left: 50%; transform: translateX(-50%);top: 60px;
				line-height: 200px;
				text-align: center;
				font-weight: 200;
				font-size: 100px;
				
				color: #1890FF;
				
	},
	.show_text {
		position: absolute;
		top: 300px;
		color: #169AF3;
		font-size: 20px;
	},
	.show_se {
		position: absolute;
		top:330px;
		color: #169AF3;
	},
	.show_tst {
		position: absolute;
		top:330px;
		left: 200px;
		color: #169AF3;
	}
	.show_sol {
		position: absolute;
		top:360px;
		
		color: #169AF3;
	},
	.show_waso {
		position: absolute;
		top:360px;
		left: 200px;
		color: #169AF3;
	}
</style>
