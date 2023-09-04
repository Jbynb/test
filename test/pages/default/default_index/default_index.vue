<template>
	<view class="main">
		<image mode="aspectFill" class="img" src="/static/home.jpg" />
		<view class="list">
			<view class="item" v-for="(item,index) in homeList" :key="index" @tap="homeClick(item.path)">
				<view class="inner">
					<image :src="item.img"></image>
					<text>{{item.title}}</text>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				homeList:[
					{
						img:"/static/menu/1.png",
						title:"公告",
						path:"/pages/news/news_index/news_index"
					
				    },{
						img:"/static/menu/2.png",
						title:"预定会议室",
						path:"/pages/enroll/enroll_detail/enroll_detail"
					},{
						img:"/static/menu/3.png",
						title:"留言",
						path:"/pages/message/message_submit/message_submit"
					},{
						img:"/static/menu/4.png",
						title:"我的预定",
						path:"/pages/my/my_reserve/my_reserve"
					}
					
				]
				
			}
		},
		
		methods: {
			homeClick(url){
				uni.navigateTo({url})
			}
			
		}
	}
</script>

<style>
	.main{
		width: 100%;
		padding: 0;
	}
	.main .img{
		width: 100%;
		height: 600rpx;
	}
	.main .list{
		position: relative;
		width: 100%;
		margin-top: -50rpx;
		background-color: #fff;
		display: flex;
		flex-wrap: wrap;
		padding: 60rpx 50rpx;
		border-top-right-radius: 50rpx;
		border-top-left-radius: 50rpx;
	}
	
	
	.main .list .item{
		width: 50%;
		margin-bottom: 30rpx;
	}
	
	.main .list .item:nth-child(odd) {
		padding-right: 15rpx;
	}
	
	.main .list .item:nth-child(even) {
		padding-left: 15rpx;
	}
	
	.main .list .item .inner{
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: #F0F2FE;
		border-radius: 20rpx;
		padding: 30rpx;
		height: 250rpx;
	}

	.main .list .item .inner image{
		width: 100rpx;
		height: 100rpx
	}

	.main .list .item .inner text{
		margin-top: 20rpx;
		font-size: 30rpx;
		color: #000;
		font-weight: bold;
	}
	
	view,
	scroll-view,
	swiper,
	button,
	input,
	textarea,
	label,
	navigator,
	image {
		box-sizing: border-box;
	} 
	
</style>
