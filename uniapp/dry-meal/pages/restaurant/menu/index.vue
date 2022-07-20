<template>
	<view>
		这是菜单
		
	</view>
</template>

<script>
	export default {
		components: {
			uniNavBar
		},
		data() {
			return {
				title: "菜单",
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

<style>
</style>