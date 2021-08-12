<template>
	<view class="zhaopin">
		<view class="topicimg">
		<image src="../../static/0.jpg" mode=""></image>
		</view>
		<view class="details">
			<view class="d-left">
				<text class="workertitle">{{this.Recruitment.name}}</text>
				<view class="tails-ailgn">
					<text>{{this.Recruitment.siteName}}</text>
					<text>{{this.Recruitment.workName}}</text>
					<text>{{this.Recruitment.workYears}}</text>
				</view>
			</view>
			<view class="d-right">
				<button type="default" @click="turntobaoming">立即报名</button>
			</view>
		</view>
		<view class="d-mid">
		<view><text>薪资待遇:  {{this.Recruitment.money}}</text></view>
		<view><text>报名方式:  {{this.Recruitment.phone}}-免费报名咨询电话</text></view>
		<view><text>招聘人数:  {{this.Recruitment.numbers}}名</text></view>
		</view>
		<view class="nav-content">
			<text :class="{'active':isActive==1}" @click="chenked(1)">赚多少钱</text>
			<text :class="{'active':isActive==2}" @click="chenked(2)">干什么活</text>
			<text :class="{'active':isActive==3}" @click="chenked(3)">伙食住宿</text>
			<text :class="{'active':isActive==4}" @click="chenked(4)">福利待遇</text>
			<text :class="{'active':isActive==5}" @click="chenked(5)">岗位要求</text>
		</view>
		<view class="nav_items">
			<view class="nav_item" v-if="isActive==1">
			{{this.Recruitment.content1}}
			</view>
			<view class="nav_item" v-if="isActive==2">
			{{this.Recruitment.content2}}
			</view>
			<view class="nav_item" v-if="isActive==3">
			{{this.Recruitment.content3}}
			</view>
			<view class="nav_item" v-if="isActive==4">
			{{this.Recruitment.content4}}
			</view>
			<view class="nav_item" v-if="isActive==5">
			{{this.Recruitment.content5}}
			</view>
		</view>
		
		
	</view>
</template>

<script>
	export default {
		data(){
			return{
				isActive: 1,
				pageid:'',
				Recruitment:[
				]
			}
		},
		methods:{
			chenked(type) {
				this.isActive = type
			},
			turntobaoming(){
				uni.navigateTo({
				    url: '../zhaopin/zhaopin'
				});
			},
			getpagedatas(){
				{
					uni.request({
					    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/recruit/content?recruit_id='+this.pageid, 
					    data: {
					    },
					    success: (res) => {
					       this.Recruitment=res.data.data.Recruitment
					    }
					});	
				}
			}
		},
		onLoad(option) {
			this.pageid=option.id;
			this.getpagedatas()
		},
	}
</script>

<style scoped>
.topicimg{
	margin-top: 10rpx;
}
.topicimg image{
	width: 100%;
	height: 300rpx;
	
}
.details{
	margin-top: 50rpx;
	display: flex;
	justify-content: space-between;
}
.d-left .workertitle{
	color: #595CF9;
	font-weight: bold;
	font-size: 35rpx;
	margin: 20rpx;
}
.tails-ailgn text{
	font-size: 30rpx;
	margin: 20rpx;
	color: #878787;
}
.d-right button{
	background-color: #F86633;
	color: #FFFFFF;
	font-size: 35rpx;
	margin-right: 20rpx;
}
.d-mid{
	margin-top: 20rpx;
	display: flex;
	flex-direction: column;
	align-items: center;
}
.d-mid view{
	width: 95%;
	height: 80rpx;
	margin: 10rpx;
	display: flex;
	align-items: center;
	color: #FFFFFF;
}
.d-mid view text{
	margin-left: 50rpx;
	margin-top: -5rpx;
}
.d-mid view:nth-child(1){
	background-color: #2AACCE;
}
.d-mid view:nth-child(2){
	background-color: #F3BD59;
}
.d-mid view:nth-child(3){
	background-color: #F07496;
}
.nav-content{
	margin-top: 30rpx;
	display: flex;
	justify-content: center;
	align-items: center;
}
.nav-content text{
	font-size: 32rpx;
	width: 135rpx;
	height: 50rpx;
	padding: 4rpx;
	border-bottom: 5rpx #E5E5E5 solid;
}
.active{
	background-color: #5C5CF2;
	color: #FFFFFF;
}

.nav-content text:nth-child(1){
	margin-left: 10rpx;
	
}
.nav-content text:nth-child(5){
	margin-right: 10rpx;
	
}
.nav_item{
	margin-top: 30rpx;
	margin-left: 50rpx;
	margin-right: 50rpx;
}
</style>
