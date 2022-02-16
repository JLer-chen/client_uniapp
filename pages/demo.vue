<template>
	<view>
		<view>
			<button @click="showload()">{{sta}}</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sta:'aja'
			}
		},
		methods: {
			showload(){
				/* uni.showToast({
					title:'iij',
					duration:2000
				}) */
				var flag=0;
			uni.showModal({
			    title: '提示',
			    content: '这是一个模态弹窗',
			    success: function (res) {
			        if (res.confirm) {
			            console.log('用户点击确定');
			        } else if (res.cancel) {
			            console.log('用户点击取消');
			        }
					flag=1;
					console.log('flag is '+flag);
			    }
			});
			setTimeout(function () {
			    // 这里就是处理的事件
			}, 5000);
				this.sta='oooo'
			}
		}
	}
</script>

<style>

</style>
