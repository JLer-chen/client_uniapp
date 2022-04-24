<template>
	<view class="text-box">
		
		
		<!-- <button @click="stop()">stop monitoring</button> -->
		<view class="shuoming">点击start进入睡眠状态</view>
		
		<view class="circle" @click="monitor()">{{state}}</view>
		
		<!-- <button @click="to_show()">showpage</button>
		<button>{{variance_total}}</button>
		<button @click="set_file()">{{statue}}</button>
		<button>count:{{count}}</button>
		<button @click="get_scale()">进入睡眠量表</button>
		<button @click="intodemo()" class="temp">{{stop_statue}}</button>
		<button @click="get_tanc()">弹窗</button> -->
			<!-- <view class="table" @click="get_scale()">睡眠量表</view>
			<view class="table1">可视化</view> -->
		<!-- <view class="little_block1"></view>
		<view class="little_block2"></view>
		<view class="little_block3"></view>
		<view class="little_block4"></view>
		<view class="little_block5"></view>
		<view class="little_block6"></view>
		<view class="little_block7"></view>
		<view class="little_block8"></view>
		<view class="little_block9"></view>
		<view class="little_block10"></view> -->
		<!-- <button @click="set_value()">change</button> -->
		<view class="charts-box">
		  <qiun-data-charts
		    type="gauge"
		    :chartData="chartData"
			:opts="opt"
		    background="none"
			
			
			 :loadingType="3"
			
		  />
		</view>
	</view>
</template>



<script>
	
	
	
	export default {
		data() {
			return {
				glo_show_cou:1,
				stop_statue:'wait',
				temp_arr:[[1,2,3]],
				state:"start",
				statue:'initial',
				variance_total:0,
				time_id:0,
				res_x:0,
				res_y:0,
				res_z:0,
				count:0,
				total_temp:0,
				arrx_25:[],
				arry_25:[],
				arrz_25:[],
				sta_arrx:[],
				sta_arry:[],
				sta_arrz:[],
				real_sta:0,
				
				chartData:{
				    "categories": [
				          {
				              "value": 0.2,
				              "color": "#1890ff"
				          },
				          {
				              "value": 0.8,
				              "color": "#2fc25b"
				          },
				          {
				              "value": 1,
				              "color": "#f04864"
				          }
				      ],
				      "series": [
				          {
				              "name": "完成率",
				              "data": 0
				          }
				      ]
				},
				opt:{
					 "title": {
					        "name": "0",
					        "fontSize": 25,
					        "color": "#2fc25b",
					        "offsetX": 0,
					        "offsetY": 50
					    },
					    "subtitle": {
					        "name": "活动幅度",
					        "fontSize": 15,
					        "color": "#1890ff",
					        "offsetX": 0,
					        "offsetY": -50
					    }
				}
				
				 }
		
		}
		,
		onShow:function(){
				console.log(uni.getStorageSync('is_login'));
				if(this.glo_show_cou==1){
					uni.setStorageSync('is_login',false);
				}
				this.glo_show_cou++;
				
		},
		methods:{
			get_tanc(){
				uni.showModal({
					 title: '提示',
					    content: '数据收集成功，点击确定完成睡眠量表',
					    success: function (res) {
					        if (res.confirm) {
					            console.log('用户点击确定');
								uni.navigateTo({
									url:"Sleep_scale/Sleep_scale"
								});
							
					        } else if (res.cancel) {
					            console.log('用户点击取消');
					        }
					    }
				});
			},
			 intodemo(){
				 uni.navigateTo({
				 	url:'/pages/demo'
				 })
			 }
			,
			to_show(){
				uni.navigateTo({
					url:"Sleep_scale/problem-widget/show"
				})
			},
		
			monitor(){
				if(uni.getStorageSync('is_login')){
					console.log(uni.getStorageSync('is_login'));
					this.arrx_25=[];
					this.arry_25=[];
					this.arrz_25=[];
					
					if(this.state=="start"){
						console.log('start');
						
						
						this.time_id=setInterval(()=>{
							var data_temp=this.chartData;
							// var rand=Math.random()*30;
							// rand=Math.floor(rand);
							console.log('var_t'+this.variance_total)
							data_temp.series[0].data=this.variance_total/100;
							var real_sta_str=Math.floor(this.variance_total);
							real_sta_str=real_sta_str.toString();
							
							console.log('data_temp_data is '+data_temp.series[0].data);
							console.log('str_ is '+real_sta_str);
							/* data_temp.series[1].data=0.5; */
							//console.log(this.chartData.series);
							this.chartData=data_temp;
							this.opt.title.name=real_sta_str;
							/* console.log(JSON.stringify(this.chartData)); */
						},1000);
						uni.startAccelerometer({
							interval:'normal'
							
						});
					  uni.onAccelerometerChange(  (res)=> {
						  var total=0;  
							/* var d=new Date(); */
						  //console.log(res.x);
						  //console.log(res.y);
						    //console.log(res.z); 
							/* console.log(typeof(res.x)); 
							console.log(typeof(this.arrx_25)); */
							 this.arrx_25.push(res.x);
							 this.sta_arrx.push(res.x);
							 this.arry_25.push(res.y);
							 this.sta_arry.push(res.y);
							 this.arrz_25.push(res.z);
							 this.sta_arrz.push(res.z);
							/* this.arry_25.append(res.y);
							this.arrz_25.append(res.z); */
							this.count=this.count+1; 
							
							if(this.count%5==0&&this.count!=0){
								var sumx=0;
								var sumy=0;
								var sumz=0;
								for(var i=0;i<5;i++){
									sumx+=this.arrx_25[i];
									sumy+=this.arry_25[i];
									sumz+=this.arrz_25[i];
								}
								var ba_x=sumx/5;
								var ba_y=sumy/5;
								var ba_z=sumz/5;
								
								var variance_x=0;
								var variance_y=0;
								var variance_z=0;
								for(var i=0;i<5;i++){
									variance_x+=Math.pow((this.arrx_25[i]-ba_x),2)/5;
									
								}
								for(var i=0;i<5;i++){
									variance_y+=Math.pow((this.arry_25[i]-ba_y),2)/5;
									
								}
								for(var i=0;i<5;i++){
									variance_z+=Math.pow((this.arrz_25[i]-ba_z),2)/5;
									
								}
								console.log('va_x is '+variance_x);
								console.log('va_y is '+variance_y);
								console.log('va_z is '+variance_z);
								
								total=(variance_x+variance_y+variance_z)/3*50000;
								if(total>1&&total<100){
									total=Math.sqrt(total+100);
								}
								if(total>100){
									total=Math.sqrt(total);
									if(total>100){
										total=100;
									}
								}
								
								if(total<1){
									total=Math.sqrt(this.variance_total+10);
								}
								console.log(total);
								this.variance_total=total;
								// console.log('total is '+total);
								// console.log('var_ta is '+this.variance_total);
								console.log('count is '+this.count);
								
								if(this.count%300==0&&this.count!=0){
															 var arr_total=new Array();
															 for(var i=0;i<300;++i){
																 arr_total[i]=new Array();
																 for(var j=0;j<3;j++){
																	 
																	 if(j==0){
																		 arr_total[i][j]=this.sta_arrx[i+this.count-300];
																		 console.log(typeof arr_total);
																	 }
																	 if(j==1){
																		 arr_total[i][j]=this.sta_arry[i+this.count-300];
																	 }
																	 if(j==2){
																	 	 arr_total[i][j]=this.sta_arrz[i+this.count-300];
																	 }
																 }
															 }
															 for(var i=0;i<300;++i){
																  this.temp_arr.push(arr_total[i]);
															 }
															console.log(this.temp_arr.length);
															 var temp_json=JSON.stringify(this.temp_arr);
															 // console.log(temp_json);
															 // console.log(typeof temp_json);
															 uni.request({
															 	url:'http://192.168.137.146:8088/post3',
															 	method:'POST',
															 	data:{
															 		test_json:temp_json
															 	},
															 	success: (res) => {
															 		
															 		if(res.data.code==1){
															 			console.log(this.count/300+': upload success');
															 			this.statue=this.count/300+': upload success';
															 		}
															 		else{
															 			console.log(this.count/300+': upload fail');
															 			this.statue=this.count/300+': upload fail';
															 		}
															 	},
															 	fail: () => {
															 		console.log(this.count/300+':~upload fail');
															 		this.statue=this.count/300+':~upload fail';
															 	}
															 })
															 // uni.setStorage({
															 // 	key:'sleep_data',
															 // 	data:arr_total,
															 // 	success: function () {
															 // 	    console.log('successful data');
															 // 	}
															 // })
								}
								
								this.arrx_25=[];
								this.arry_25=[];
								this.arrz_25=[];
								
							 }
							
						});
						
						this.state="end";
						console.log('arrx is '+this.arrx_25);
					}
					else{
						// clearInterval(this.time_id);
						var data_temp=this.chartData;
						data_temp.series[0].data=0;
						this.chartData=data_temp;
						this.opt.title.name='0';
						console.log('stop monitoring');
						/* uni.stopAccelerometer({
							success: () => {
								this.stop_statue='stop_success'
							}
						}); */
					
						
						this.state="start";
						
						//发送数据
						// var arr_total=new Array();
						// console.log(this.count-this.temp_arr.length+1);
						// for(var i=0;i<this.count-this.temp_arr.length+1;i++){
						// 		 arr_total[i]=new Array();
						// 		 for(var j=0;j<3;j++){
																						 
						// 				 if(j==0){
						// 						arr_total[i][j]=this.sta_arrx[i+this.temp_arr.length-1];
						// 						 //console.log(arr_total[i][j]);
						// 						}
						// 				 if(j==1){
						// 							 arr_total[i][j]=this.sta_arry[i+this.temp_arr.length-1];
						// 								}
						// 				if(j==2){
						// 						 arr_total[i][j]=this.sta_arrz[i+this.temp_arr.length-1];
						// 						 }
						// 						}
						// }
						//     var cc=this.count-this.temp_arr.length+1;
						// for(var i=0;i<cc;++i){	
							
						// 	this.temp_arr.push(arr_total[i]);
						// }
						// var temp_json=JSON.stringify(this.temp_arr);
						// //console.log(temp_json);
						// console.log(typeof temp_json);
						// uni.request({
						// 	url:'http://192.168.31.185:8088/post4',
						// 	method:'POST',
						// 	data:{
						// 		test_json:temp_json
						// 	},
						// 	success: (res) => {
						// 		console.log(res.data);
						// 		if(res.data.code==1){
						// 			console.log('final_upload success');
						// 			this.statue='final_upload success';
						// 			uni.showModal({
						// 				 title: '提示',
						// 				    content: '数据收集成功，点击确定完成睡眠量表',
						// 				    success: function (res) {
						// 				        if (res.confirm) {
						// 				            console.log('用户点击确定');
						// 							uni.navigateTo({
						// 								url:"Sleep_scale/Sleep_scale"
						// 							});
												
						// 				        } else if (res.cancel) {
						// 				            console.log('用户点击取消');
						// 				        }
						// 				    }
						// 			});
						// 			this.statue='fff'
						// 			console.log('ffff');
						// 		}
						// 		else{
						// 			console.log('final_upload fail');
						// 			this.statue='final_upload fail';
						// 		}
						// 	},
						// 	fail: () => {
						// 		console.log('final_upload fail');
						// 		this.statue='final_upload fail';
						// 	}
						// });
						uni.showModal({
							 title: '提示',
							    content: '数据收集成功，点击确定完成睡眠量表',
							    success: function (res) {
							        if (res.confirm) {
							            console.log('用户点击确定');
										uni.navigateTo({
											url:"Sleep_scale/Sleep_scale"
										});
									
							        } else if (res.cancel) {
							            console.log('用户点击取消');
							        }
							    }
						});
						
						
					}
				}
				else{
					uni.showModal({
						 title: '提示',
						    content: '请先登入',
						    success: function (res) {
						        if (res.confirm) {
						            console.log('用户点击确定');
									
								
						        } else if (res.cancel) {
						            console.log('用户点击取消');
						        }
						    }
					});
				}
				
			},
			
			get_scale(){
				uni.navigateTo({
					url:"Sleep_scale/Sleep_scale"
				})
			}
		}
		
		
		}
</script>

<style  lang="scss">
	.charts-box {
		
		  width: 100%;
		  height: 300px;
		  position: relative;
		  top: 400px;
			
	}
	.index_box{
		text-align: center;
		margin: 10px 10px;
	}
	.status{
		font-size: small;
		color: #808080;
		text-align:center;
	}
	.shuoming{
		text-align: center;
		letter-spacing: 5px;
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
	.icon{
		width: 80px;
		height: 90px;
		margin-right: 100px;
	}
	.biao{
		
	}
	.circle {
	  border-radius: 50%;
	  width: 300px;
	  height: 300px;
	  background: #0fbfc8;
		position: absolute; left: 50%; transform: translateX(-50%);
		//top: 150px;//top可以注释
		line-height: 300px;
		text-align: center;
		font-weight: 300;
		font-size: 100px;
		font-style: italic;
		color: #F8F8F8;
	}
	.table {
		border-radius: 30%;
		width: 150px;
		height: 300px;
		background: #ffff00;
		position: relative;
		top: 300px;
		left: 30px;
		text-align: center;
		font-weight: 300;
		font-size: 30px;
		font-style: italic;
		color: #F8F8F8;
		line-height: 300px;
	}
	.temp {
		position: relative;top: 300px;
	}

</style>
