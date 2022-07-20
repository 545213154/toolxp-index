<template>
	<view class="example-body">
		<uni-nav-bar :fixed="false" color="#333333" backgroundColor="#FFFFFF" rightIcon="scan" >
			<!-- <block v-slot="left">
				<view>
					<view><text class="input-uni-nav-bar-text"> 福州 </text></view>
					<uni-icons type="arrowdown" color="#333333" size="22"></uni-icons>
				</view>
			</block> -->
			<view class="input-view">
				<uni-icons class="input-uni-icon" type="search" size="22" color="#333333"></uni-icons>
				<input class="nav-bar-input" type="text" placeholder="输入关键字" confirm-type="search"/>
			</view>
		</uni-nav-bar>
		<text v-for="(item,index) in list"> {{item.url}} </text>
		<button @click="to"> 跳转页面 </button>
		<web-view src="https://www.bilibili.com/video/BV11U4y1Z7vR?p=16&spm_id_from=pageDriver&vd_source=f45cd9a507c8a2c79bfd3558eb495e10"></web-view>
	</view>
</template>

<script>
	import uniNavBar from "@/uni_modules/uni-nav-bar/components/uni-nav-bar/uni-nav-bar.vue"
	
	export default {
		components: {
			uniNavBar
		},
		data() {
			return {
				title: "首页",
				list: []
			}
		},
		onLoad() {
			
		},
		mounted() {
			uni.request({
				url:"http://html5.bjsxt.cn/api/index/banner",
				success: (res)=>{
					this.list = res.data
				}
			})
		},
		methods:{
			to(){
				console.log("跳转");
				uni.switchTab({
					url: "/pages/restaurant/menu"
				})
				console.log("跳转过了");
			}
		}
	}
</script>

<style lang="scss">
	.input-view {
		display: flex;//子元素水平摆放
		flex-direction: row;
		flex: 1;
		background-color: #f8f8f8;
		height: 30px;
		border-radius: 15px;
		padding: 0 15px;
		flex-wrap: nowrap;
		margin: 7px 0;
		line-height: 30px;

	}
	.input-uni-icon {
		line-height: 30px;
	}
	.nav-bar-input {
		height: 30px;
		line-height: 30px;
		width: 370rpx;
		padding: 0 5px;
		font-size: 28rpx;
		background-color: #f8f8f8;
	}
	.example-body {
		padding: 0;
	}
</style>
