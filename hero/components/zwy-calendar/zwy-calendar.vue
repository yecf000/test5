<template>
	<view class="mydec">
	<view class="calendar-box">
		<view class="month">
			<view>{{enmonth}}</view>
		</view>
		<view class="week">
			<view  v-for="weeks in weekArr">{{weeks}}</view>
		</view>
		<view class="day">
			<view 
				v-for="(days,index) in dayArr" :key="index">
				{{days.day}}
			</view>
		</view>
		<view class="pagebutton">
			<button type="default">签到</button>
			<button type="default">积分明细</button>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		props: {
			lang: {
				type: String,
				default: 'EN'
			},
			type: {
				type: String,
				default: 'calendar'
			},
			checkDate: {
				type: Boolean,
				default: false
			},
			bgweek: {
				type: String,
				default: '#FF8F22'
			},
			bgday: {
				type: String,
				default: '#FF8F22'
			}
		},
		data() {
			return {
				enmonth:'',
				weeked: '', // 今天周几
				dayArr: [], // 当前月每日
				localDate: '', // 今天日期
				day: new Date().getDate(), // 当前日
				year: new Date().getFullYear(), // 当前年
				month: new Date().getMonth() + 1, // 当前月
				weekArr: ['日', '一', '二', '三', '四', '五', '六'], // 每周
			}
		},
		mounted() {
			let that = this;
			// 初始日期
			that.initDate();
			// 今天日期
			that.localDate = that.year + '-' + that.formatNum(that.month) + '-' + that.formatNum(that.day);
			// 中英切换
			if (that.lang != 'zh') that.weekArr = ['Su', 'Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa'];
			// 今天周几
			that.weeked = that.weekArr[new Date().getDay()];
			// 签到功能
			if (that.type != 'calendar') {
				for (let i in that.dayArr) {
					that.$set(that.dayArr[i], 'flag', false);
				}
			}
			
			this.initmonth()
		},
		methods: {
			// 初始化日期
			initDate() {
				let that = this;
				that.dayArr = [];
				// 当前月总天数
				let totalDay = new Date(that.year, that.month, 0).getDate();
				// 遍历总天数将日期逐个添加至数组
				for (let i = 1; i <= totalDay; i++) {
					// 得到需补充天数
					let value = (new Date(that.year, that.month - 1, i)).getDay();
					// 补充前面空白日期
					if (i == 1 && value != 0) that.addBefore(value);
					// 添加本月日期
					let obj = {};
					obj.date = that.year + '-' + that.formatNum(that.month) + '-' + that.formatNum(i);
					obj.day = i;
					that.dayArr.push(obj);
					// 补充后面空白日期
					if (i == totalDay && value != 6) that.addAfter(value);
				}
			},
			// 补充前面空白日期
			addBefore(value) {
				let that = this;
				let totalDay = new Date(that.year, that.month - 1, 0).getDate();
				for (let i = 0; i < value; i++) {
					let obj = {};
					obj.date = '';
					obj.day = totalDay - (value - i) + 1;
					that.dayArr.push(obj);
				}
			},
			// 补充后空白日期
			addAfter(value) {
				let that = this;
				for (let i = 0; i < (6 - value); i++) {
					let obj = {};
					obj.date = '';
					obj.day = i + 1;
					that.dayArr.push(obj);
				}
			},
			// 格式化日期位数
			formatNum(num) {
				return num < 10 ? ('0' + num) : num;
			},
			initmonth(){
				if(this.month=="1"){
					this.enmonth = "January"
				}
				if(this.month=="2"){
					this.enmonth = "February"
				}
				if(this.month=="3"){
					this.enmonth = "March"
				}
				if(this.month=="4"){
					this.enmonth = "April"
				}
				if(this.month=="5"){
					this.enmonth = "May"
				}
				if(this.month=="6"){
					this.enmonth = "June"
				}
				if(this.month=="7"){
					this.enmonth = "July"
				}
				if(this.month=="8"){
					this.enmonth = "August"
				}
				if(this.month=="9"){
					this.enmonth = "September"
				}
				if(this.month=="10"){
					this.enmonth = "October"
				}
				if(this.month=="11"){
					this.enmonth = "November"
				}
				if(this.month=="12"){
					this.enmonth = "December"
				}
			}
		}
	}
</script>

<style scoped>
	.mydec{
		margin-left: 75rpx;
		width: 80%;
		background-color: #F7F7F7;
	}
	.calendar-box {
		width: 100%;
		flex-direction: column;
		justify-content: center;
	}

	.calendar-box,
	.month,
	.week,
	.day {
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.month,
	.week,
	.day {
		width: 500rpx;
	}

	.month {
		margin: 10rpx 0;
		position: relative;
	}
	.month view{
		color: #5C5CF2;
		font-size: 55rpx;
		margin: 0 auto;
	}

	.picker {
		width: 130rpx;
		height: 40rpx;
		position: absolute;
		top: 20rpx;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	.day {
		flex-wrap: wrap;
		color: #CCCCCC;
	}
	.week view{
	color: #FFFFFF;
	margin: 5rpx;
	background-color: #5C5CF2;
}
	.week>view,
	.day>view {
		width: 70rpx;
		height: 70rpx;
		text-align: center;
		position: relative;
		line-height: 60rpx;
		margin-top: 15rpx;
	}

	.checkday {
		color: #999;
	}

	.choose {
		color: #FFFFFF;
		border-radius: 50%;
	}


	.sign {
		background-color: #0089fe;
	}

	.repair {
		background-color: #f4a01a;
	}
	.pagebutton{
		display: flex;
		justify-content: space-around;
	}
	.pagebutton button{
		background-color: #5C5CF2;
		color: #FFFFFF;
		font-size: 25rpx;
		width: 200rpx;
		margin: 30rpx;
	}
</style>
