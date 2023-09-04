<template>
	<view>
		<button @tap="mainTap">留言</button>
		
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
					uni.navigateTo({url:"/pages/message/message_submit/message_submit"})
				}
			
		}
	}
</script>

<style>

</style>
