<template>
    <view class="content">
        <view class="row b-b">
            <text class="tit">申请项目</text>
            <input class="input" type="text" v-model="reserveData.project" placeholder="  项目" placeholder-class="placeholder" />
        </view>
        <view class="row b-b">
            <text class="tit">使用人数</text>
            <input class="input" type="number" v-model="reserveData.num" placeholder="  使用人数" placeholder-class="placeholder" />
        </view>
		<view class="row b-b">
		    <text class="tit">所属单位</text>
		    <input class="input" type="text" v-model="reserveData.unit" placeholder="  所属单位" placeholder-class="placeholder" />
		</view>
		<view class="row b-b">
		    <text class="tit">联系人</text>
		    <input class="input" type="text" v-model="reserveData.name" placeholder="  联系人" placeholder-class="placeholder" />
		</view>
		<view class="row b-b">
		    <text class="tit">联系电话</text>
		    <input class="input" type="tel" maxlength=11 v-model="reserveData.phone" placeholder="  联系电话" placeholder-class="placeholder" />
		</view>
		<view class="row b-b">
		    <text class="tit">项目介绍</text> 
			
		</view>
		
        <textarea class="inputArea" v-model="reserveData.introduce" />
        <button class="add-btn" @click="confirm">提交</button>
		<view>{{addressData.lab}}</view>
    </view>
</template>
 
<script>
    export default {
        data() {
            return {
                reserveData: {
                    lab: '',
					startTime:'',
					endTime:'',
                    project: '',
                    num: '',
					unit:'',
					name:'',
					phone:'',
                    introduce: '',
                },
				laa:'',
            }
        },
        onLoad(option) {
			this.getData(option.lab,option.startTime,option.endTime);
			
		},
        methods: {
			getData(lab,startTime,endTime){
				this.reserveData.lab=lab;
				this.reserveData.startTime=startTime;
				this.reserveData.endTime=endTime;
				
			},
			//提交
            confirm() {
				let that = this;
				if (!that.reserveData.project) {
					uni.showToast({
						title: '请输入申请的项目',
						icon: 'none'
					});
					return;
				}
				if (!that.reserveData.num) {
					uni.showToast({
						title: '请输入使用人数',
						icon: 'none'
					});
					return;
				}
				if (!that.reserveData.unit) {
					uni.showToast({
						title: '请输入单位',
						icon: 'none'
					});
					return;
				}
				if (!that.reserveData.name) {
					uni.showToast({
						title: '请输入联系人',
						icon: 'none'
					});
					return;
				}
				if (!that.reserveData.phone) {
					uni.showToast({
						title: '请输入联系电话',
						icon: 'none'
					});
					return;
				}
                let data = this.reserveData;
                console.log(JSON.stringify(data))
            },
        }
    }
</script>
 
<style lang="scss">
    page {
        padding-top: 16upx;
    }
 
    .row {
        display: flex;
        align-items: center;
        position: relative;
        padding: 0 30upx;
        height: 110upx;
        background: #fff;
 
        .tit {
            flex-shrink: 0;
            width: 120upx;
            font-size: 30upx;
 
        }
 
        .input {
            flex: 1;
            font-size: 30upx;
 
        }
		
 
        .icon-shouhuodizhi {
            font-size: 36upx;
 
        }
		
    }
	.inputArea{
		border-style: inset;
		margin-left: 15px;
		margin-right: 90px;
		
	
	}


 
    .add-btn {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 690upx;
        height: 80upx;
        margin: 60upx auto;
        background-color: rgb(28, 42, 134);
        color: #fff;
 
        border-radius: 10upx;
        box-shadow: 1px 2px 5px rgba(28, 42, 134, 0.4);
		
    }
</style>
 