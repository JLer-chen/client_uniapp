<template>
	<view class="TEL_box"> 
		<view class="">
			TEL:
		</view>
		<view>
			<input type="text" v-model="telnumber" />
		</view>
		<view class="fanhui">
			保存
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				telnumber:''
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.TEL_box{
		margin: 10px 10px;
	}
	
</style>
