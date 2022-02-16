<template>
	<view class="pages" v-if="viewModel">
		<pages-rate :percent="percent"></pages-rate>
		<view class="pages-line"></view>
		<view class="cont" v-if="widget">
			<view class="cont-title">{{widget.title}} <text class="cont-require" v-if="widget.required">*</text></view>
			<!-- <view class="cont-intro">信息仅用于推荐产品</view> -->
			<view class="select" v-if="widget.type === 'radio'">
				<view class="select-btn" @click="selectClick(widget.answer, item)" v-for="(item, index) in widget.answer" :key="index">{{item.name}}</view>
			</view>
			<view class="input" v-if="widget.type === 'input'">
				<!-- <view class="input-title">{{widget.intro}}</view> -->
				<input type="text" @focus="isFocus = true" @blur="isFocus = false" v-model="value" placeholder-class="input-place" class="input-cont" :class="{'input-contact': isFocus}" :placeholder="widget.placeholder" />
				<view class="input-tips">输入内容越详细，结果越精准</view>
				<view class="input-submit" @click="nextClick">下一步</view>
			</view>
		</view>
		<pages-msg v-if="viewIndex == viewModel.length" :userInfo="userInfo"></pages-msg>
	</view>
</template>

<script>
	import pagesRate from './problem-widget/rate'
	import pagesMsg from './problem-widget/msg'
	import testJson from './problem-widget/test.json'
	export default {
		data() {
			return {
				percent: 0,
				problemList: testJson.problem, // 所有问题
				viewModel: null,  //需展现问题
				widget: {}, // 问题对象
				viewIndex: 0 ,// 当前所处问题下标
				value: '',
				userInfo: {} ,// 登录用户
				problemModel: null ,// 已完成问题
				isFocus: false,
				one: 0,
				two: 0,
				three:0,
				four:0,
				five_a:0,
				five_b:0,
				five_c:0,
				five_d:0,
				five_e:0,
				five_f:0,
				five_g:0,
				five_h:0,
				five_i:0,
				five_j:0,
				six:0,
				seven:0,
				eight:0,
				nine:0,
				sum:0,
				sum_a:0,
				sum_b:0,
				sum_c:0,
				sum_d:0,
				sum_e:0,
				sum_f:0,
				sum_g:0
			}
		},
		components: {
			pagesRate,
			pagesMsg
		},
		onLoad() {
			this.init()
		},
		methods: {
			async init() {
				this.viewModel = JSON.parse(JSON.stringify(this.problemList))
				this.widget = this.viewModel[this.viewIndex]
			},
			selectClick(data, item) {
				this.radioHandle(data, item)
			},
			// 选择处理
			radioHandle(source, item) {
				// 获取已执行完内容
				//console.log(source)
				console.log(item.name)
				console.log('1 '+this.viewIndex)
				//record the data by index
				if(this.viewIndex==4){
					 if(item.name=='⑴无'){
						 this.five_a=0
					 }
					 if(item.name=='⑵〈1次/周'){
						 this.five_a=1
					 }
					 if(item.name=='⑶1-2次/周'){
					 	 this.five_a=2
					 }
					 if(item.name=='⑷≥ 3次/周'){
						 this.five_a=3
					 }
					 console.log('five_a is '+this.five_a)
					 
				 }
				if(this.viewIndex==5){
					 if(item.name=='⑴无'){
						 this.five_b=0
					 }
					 if(item.name=='⑵〈1次/周'){
						 this.five_b=1
					 }
					 if(item.name=='⑶1-2次/周'){
					 	 this.five_b=2
					 }
					 if(item.name=='⑷≥ 3次/周'){
						 this.five_b=3
					 }
					 console.log('five_b is '+this.five_b)
				 }
				 if(this.viewIndex==6){
				 	 if(item.name=='⑴无'){
				 		 this.five_c=0
				 	 }
				 	 if(item.name=='⑵〈1次/周'){
				 		 this.five_c=1
				 	 }
				 	 if(item.name=='⑶1-2次/周'){
				 	 	 this.five_c=2
				 	 }
				 	 if(item.name=='⑷≥ 3次/周'){
				 		 this.five_c=3
				 	 }
				 	 console.log("five_c is"+' '+this.five_c)
				  }
				  if(this.viewIndex==7){
				  	 if(item.name=='⑴无'){
				  		 this.five_d=0
				  	 }
				  	 if(item.name=='⑵〈1次/周'){
				  		 this.five_d=1
				  	 }
				  	 if(item.name=='⑶1-2次/周'){
				  	 	 this.five_d=2
				  	 }
				  	 if(item.name=='⑷≥ 3次/周'){
				  		 this.five_d=3
				  	 }
				  	 console.log("five_d is"+' '+this.five_d)
				   }
				   if(this.viewIndex==8){
				   	 if(item.name=='⑴无'){
				   		 this.five_e=0
				   	 }
				   	 if(item.name=='⑵〈1次/周'){
				   		 this.five_e=1
				   	 }
				   	 if(item.name=='⑶1-2次/周'){
				   	 	 this.five_e=2
				   	 }
				   	 if(item.name=='⑷≥ 3次/周'){
				   		 this.five_e=3
				   	 }
				   	 console.log("five_e is"+' '+this.five_e)
				    }
					if(this.viewIndex==9){
						 if(item.name=='⑴无'){
							 this.five_f=0
						 }
						 if(item.name=='⑵〈1次/周'){
							 this.five_f=1
						 }
						 if(item.name=='⑶1-2次/周'){
						 	 this.five_f=2
						 }
						 if(item.name=='⑷≥ 3次/周'){
							 this.five_f=3
						 }
						 console.log("five_f is"+' '+this.five_f)
					 }
					 if(this.viewIndex==10){
					 	 if(item.name=='⑴无'){
					 		 this.five_g=0
					 	 }
					 	 if(item.name=='⑵〈1次/周'){
					 		 this.five_g=1
					 	 }
					 	 if(item.name=='⑶1-2次/周'){
					 	 	 this.five_g=2
					 	 }
					 	 if(item.name=='⑷≥ 3次/周'){
					 		 this.five_g=3
					 	 }
					 	 console.log("five_g is"+' '+this.five_g)
					  }
					  if(this.viewIndex==11){
					  	 if(item.name=='⑴无'){
					  		 this.five_h=0
					  	 }
					  	 if(item.name=='⑵〈1次/周'){
					  		 this.five_h=1
					  	 }
					  	 if(item.name=='⑶1-2次/周'){
					  	 	 this.five_h=2
					  	 }
					  	 if(item.name=='⑷≥ 3次/周'){
					  		 this.five_h=3
					  	 }
					  	 console.log("five_h is"+' '+this.five_h)
					   }
					   if(this.viewIndex==12){
					   	 if(item.name=='⑴无'){
					   		 this.five_i=0
					   	 }
					   	 if(item.name=='⑵〈1次/周'){
					   		 this.five_i=1
					   	 }
					   	 if(item.name=='⑶1-2次/周'){
					   	 	 this.five_i=2
					   	 }
					   	 if(item.name=='⑷≥ 3次/周'){
					   		 this.five_i=3
					   	 }
					   	 console.log("five_i is"+' '+this.five_i)
					    }
						if(this.viewIndex==14){
							 if(item.name=='⑴很好'){
								 this.six=0
							 }
							 if(item.name=='⑵较好'){
								 this.six=1
							 }
							 if(item.name=='⑶较差'){
							 	 this.six=2
							 }
							 if(item.name==' ⑷很差'){
								 this.six=3
							 }
							 console.log("six is"+' '+this.six)
						 }
						 if(this.viewIndex==13){
						 	 if(item.name=='⑴无'){
						 		 this.five_j=0
						 	 }
						 	 if(item.name=='⑵〈1次/周'){
						 		 this.five_j=1
						 	 }
						 	 if(item.name=='⑶1-2次/周'){
						 	 	 this.five_j=2
						 	 }
						 	 if(item.name=='⑷≥ 3次/周'){
						 		 this.five_j=3
						 	 }
						 	 console.log("five_j is"+' '+this.five_j)
							 var cout
							 cout=this.five_b+this.five_c +this.five_d+this.five_f+this.five_e+this.five_g+this.five_h+this.five_i+this.five_j
							 if(cout==0){
								 this.sum_e=0
							 }
							 if(cout>0&&cout<10){
								 this.sum_e=1
							 }
							 if(cout>=10&&cout<19){
							 	this.sum_e=2
							 }
							 if(cout>=19&&cout<28){
							 	 this.sum_e=3
							 }
							 console.log('sume is '+this.sum_e)
						  }
						  if(this.viewIndex==15){
						  	 if(item.name=='⑴无'){
						  		 this.seven=0
						  	 }
						  	 if(item.name=='⑵〈1次/周'){
						  		 this.seven=1
						  	 }
						  	 if(item.name=='⑶1-2次/周'){
						  	 	 this.seven=2
						  	 }
						  	 if(item.name=='⑷≥ 3次/周'){
						  		 this.seven=3
						  	 }
						  	 console.log("seven is"+' '+this.seven)
						   }
						   if(this.viewIndex==16){
						   	 if(item.name=='⑴无'){
						   		 this.eight=0
						   	 }
						   	 if(item.name=='⑵〈1次/周'){
						   		 this.eight=1
						   	 }
						   	 if(item.name=='⑶1-2次/周'){
						   	 	 this.eight=2
						   	 }
						   	 if(item.name=='⑷≥ 3次/周'){
						   		 this.eight=3
						   	 }
						   	 console.log("eight is"+' '+this.eight)
						    }
							if(this.viewIndex==17){
								 if(item.name=='⑴没有'){
									 this.nine=0
								 }
								 if(item.name=='⑵偶尔有'){
									 this.nine=1
								 }
								 if(item.name=='⑶有时候'){
								 	 this.nine=2
								 }
								 if(item.name=='⑷经常'){
									 this.nine=3
								 }
								 console.log("nine is"+' '+this.nine)
								 
								 this.sum_a=this.six
								 this.sum_f=this.seven
								 
								 if(this.five_a+this.two==0){
									 this.sum_b=0
								 }
								 if(this.five_a+this.two==1 || this.five_a+this.two==2){
								 									 this.sum_b=1
								 }
								 if(this.five_a+this.two==3 || this.five_a+this.two==4){
								 									 this.sum_b=2
								 }
								 if(this.five_a+this.two==5 || this.five_a+this.two==6){
								 									 this.sum_g=3
								 }
								 if(this.eight+this.nine==0){
								 									 this.sum_g=0
								 }
								 if(this.eight+this.nine==1 || this.eight+this.nine==2){
								 									 this.sum_g=1
								 }
								 if(this.eight+this.nine==3 || this.eight+this.nine==4){
								 									 this.sum_g=2
								 }
								 if(this.eight+this.nine==5 || this.eight+this.nine==6){
								 									 this.sum_f=3
								 }
								 this.sum_c=this.four
								 
								 this.sum=this.sum_a+this.sum_b+this.sum_c+this.sum_d+this.sum_e+this.sum_f+this.sum_g
								 console.log('sum is '+this.sum)
								 uni.setStorage({
								 	key:'total score',
									data:this.sum,
									success:function(){
										console.log('set sum')
									}
									
								 })
							 }
				var oldData = this.viewModel.slice(0, this.viewIndex + 1) 
				// 获取未执行内容
				//console.log(oldData)
				var newData = this.viewModel.slice(this.viewIndex + 1)
				var newList = newData
				//this code function is that select specific item by the before item
				/* if (item.id) {
					// 获取单选项未选择数据，暂时仅支持二选一
					var noModel = source.filter(r => r.id && r.id != item.id)
					// 获取需要排除key
					var keyList = []
					for (let i = 0; i < noModel.length; i++) {
						keyList = [...keyList, ...this.recData(newData, noModel[i], [])]
					}
					if (keyList.length > 0) {
						keyList.forEach((item, index) => keyList[index] = `'${item}'!= parantWindows `)
						// 将js 字符串转化为js 
						var newFunc = new Function('parantWindows', 'return ' + keyList.join('&&'))
						// 排除多余数据，
						newList = newData.filter(r => {
							if (newFunc(r.parentId)) return r
						})
					}
				} */
				this.viewModel = [...oldData, ...newList]
				this.viewIndex += 1
				this.widget = this.viewModel[this.viewIndex]
				this.percent = parseInt(this.viewIndex / this.viewModel.length * 100)
			},
			//recData only execute in if(item.id)
			recData(data, model, list) {
				if (data.length > 0) {
					data.forEach(item => {
						if (model && item.parentId === model.id) {
							var findModel = list.find(r => r === item.parentId)
							if (!findModel) list.push(item.parentId)
							if (item.type === 'radio') {
								var arrList = item.answer.filter(r => r.id)
								if (arrList.length > 0) {
									arrList.forEach(rr => {
										this.recData(data, rr, list)
									})
								}
							}
						}
					})
				}
				return list
			},
			nextClick() {
				if (this.widget.required && !this.value) {
					return dt.showToast('该项为必填')
				}
				
				if(this.viewIndex==0){
					this.one=this.value
					console.log('one is '+this.one)
					console.log(this.problemList)
				}
				if(this.viewIndex==1){
					this.two=this.value
					console.log('two is '+this.two)
					if(this.two<=15){
														 this.two=0
					}
					if(this.two<=30&&this.two>15){
						this.two=1
					}
					if(this.two<=60&&this.two>30){
						this.two=2
					}
					if(this.two>60){
					   this.two=3
					}
					console.log('two is '+this.two)
				}
				if(this.viewIndex==2){
					this.three=this.value
					console.log('three is '+this.three)
				}
				if(this.viewIndex==3){
					this.four=this.value
					console.log('four is '+this.four)
					console.log(Number(this.three)+24-Number(this.one))
				
					 if(Number(this.four)/(Number(this.three)+24-Number(this.one))*100>85){
						 this.sum_d=0
					 }
					 if(Number(this.four)/(Number(this.three)+24-Number(this.one))*100<=85&&Number(this.four)/(Number(this.three)+24-Number(this.one))*100>75){
					 						 this.sum_d=1
					 }
					 if(Number(this.four)/(Number(this.three)+24-Number(this.one))*100<=75&&Number(this.four)/(Number(this.three)+24-Number(this.one))*100>65){
					 						 this.sum_d=2
					 }
					 if(Number(this.four)/(Number(this.three)+24-Number(this.one))*100<65){
					 						 this.sum_d=3
					 }
					 console.log('sumd is '+this.sum_d)
					//在转化之前要想计算sumd
					if(this.four<5){
								 this.four=3
					}
					if(this.four<=6&&this.four>5){
						this.four=2
					}
					if(this.four<=7&&this.four>6){
						this.four=1
					}
					if(this.four>7){
					   this.four=0
					}
					console.log('four is '+this.four)
				}
				
				this.viewIndex += 1
				this.widget = this.viewModel[this.viewIndex]
				this.percent = parseInt(this.viewIndex / this.viewModel.length * 100)
				this.value = ''
			}
		}
	}
</script>

<style lang="scss" scoped>
	.pages {
		&-line {
			height: 50rpx;
		}
		.cont {
			width: 750rpx;
			padding: 0 30rpx;
			box-sizing: border-box;
			&-title {
				font-size: 40rpx;
				color: #222222;
				font-weight: bold;
				height: 80rpx;
				line-height: 80rpx;
			}
			&-intro {
				font-size: 32rpx;
				color: #868686;
			}
			&-require {
				margin-left: 5rpx;
				color: red;
			}
		}
		.select {
			margin-top: 120rpx;
			&-btn {
				width: 600rpx;
				height: 88rpx;
				margin: 0 auto;
				margin-bottom: 40rpx;
				border-radius: 60rpx;
				text-align: center;
				line-height: 88rpx;
				font-size: 32rpx;
				color: #222222;
				border: 1rpx solid #CCCCCC;
			}
		}
		.input {
			margin-top: 120rpx;
			&-title {
				font-size: 26rpx;
				color: #868686;
			}
			&-cont {
				margin-top: 30rpx;
				height: 100rpx;
				line-height: 100rpx;
				font-size: 32rpx;
				color: #343434;
				border-bottom: 1rpx solid #f6f7f8;
			}
			&-contact {
				border-bottom: 1rpx solid #222;
			}
			&-tips {
				margin-top: 20rpx;
				font-size: 28rpx;
				color: #868686;
			}
			&-place {
				color: #c9c9c9;
			}
			&-submit {
				width: 600rpx;
				height: 88rpx;
				margin: 0 auto;
				margin-top: 80rpx;
				background-color: #0A58F6;
				border-radius: 60rpx;
				text-align: center;
				line-height: 88rpx;
				font-size: 32rpx;
				color: #fff;
				font-weight: bold;
			}
		}
	}
</style>
