<!-- 本示例未包含完整css，获取外链css请参考上文，在hello uni-app项目中查看 -->
<template>
	<view>
		<view class="uni-title uni-common-pl">选择实验室</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-left">
					当前选择
				</view>
				<view class="uni-list-cell-db">
					<picker @change="bindPickerChange" :value="index" :range="array">
						<view class="uni-input">{{array[index].name}}</view>
					</picker>
				</view>
			</view>
		</view>
		
		<view class="uni-title uni-common-pl">选择日期</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-left">
					当前选择
				</view>
				<view class="uni-list-cell-db">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<view class="uni-input">{{date}}</view>
					</picker>
				</view>
			</view>
		</view>

		<view class="uni-title uni-common-pl">预定时间</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-left">
					当前选择
				</view>
				<view class="uni-list-cell-db">
					<picker mode="time" :value="startTime" start="09:00" end="21:00" @change="bindstartTimeChange">
						<view class="uni-input">{{startTime}}</view>
					</picker>
				</view>
				<view class="uni-list-cell-db">
					<picker mode="time" :value="endTime" start="09:00" end="21:00" @change="bindendTimeChange">
						<view class="uni-input">{{endTime}}</view>
					</picker>
				</view>
			</view>
		</view>	
		<button class="add-btn" @click="confirm">提交</button>

	</view>
</template>


<script>
export default {
    data() {
        const currentDate = this.getDate({
            format: true
        })
        return {
            title: 'picker',
            array: [{id:'01',name:'209实验室'},{id:'02',name:'111111'}],
            index: 0,
            date: currentDate,
            startTime: '09:00',
			endTime: '18:00',
			list:[],
			list_name:[]
        }
    },
	mounted(){
		for (var i in this.array){		
			this.list_name[i] = this.array[i].name
			console.log(this.list_name[i]);
		};
		
		this.getLab();
	},
	
    computed: {
        startDate() {
            return this.getDate('start');
        },
        endDate() {
            return this.getDate('end');
        }
    },
	
    methods: {
		confirm(){
			uni.navigateTo({url:"/pages/enroll/enroll_join/enroll_join?startTime="+this.start()+"&&endTime="+this.end()+"&&lab="+this.array[this.index].id})
		},
		
		start(){
			return this.date + " " + this.startTime
		},
		end(){
			return this.date + " " + this.endTime
		},
		getLab(){
			uni.request({
				url: getApp().globalData.baseUrl+'train/tEquipment/listAll',
				method: 'GET',
				header: {
					'content-type': 'application/json' // 默认值
				},
				success:(res)=> {
					console.log(res.data.result)//打印到控制台
					this.list = res.data.result
				},
				fail:(res)=>{
					console.log("失败")
				}
			})
		},
		
        bindPickerChange: function(e) {
            console.log('picker发送选择改变，携带值为', e.detail.value)
            this.index = e.detail.value
        },
        bindDateChange: function(e) {
            this.date = e.detail.value
        },
        bindstartTimeChange: function(e) {
            this.startTime = e.detail.value
        },
		bindendTimeChange: function(e) {
			this.endTime = e.detail.value
		},
        getDate(type) {
            const date = new Date();
            let year = date.getFullYear();
            let month = date.getMonth() + 1;
            let day = date.getDate();

            if (type === 'start') {
                year = year;
            } else if (type === 'end') {
                year = year + 2;
            }
            month = month > 9 ? month : '0' + month;
            day = day > 9 ? day : '0' + day;
            return `${year}-${month}-${day}`;
        }
    }
}
</script>
<style>
	
	@import '../../../common/uni.css',
	

</style>

