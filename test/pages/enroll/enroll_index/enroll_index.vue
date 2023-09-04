<template>
	<view class="main">
		<view>
			<button @tap="mainTap">预定</button>
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
			mainTap(){
					uni.navigateTo({url:"/pages/enroll/enroll_detail/enroll_detail"})
				}
		}
	}
</script>

<style>
	
</style>
