<template>
	<view class="rank">
		<view class="top-info">
			<view class="touxiang">
				
			</view>
			<view class="info">
				<view class="info1">
					<text>黄黄黄</text>
					<text>目前排名22名</text>
				</view>
				<view class="info2">
					<text>本月录取人数:{{100}}人</text>
					<text>本月预计积分:{{2000}}分</text>
				</view>
			</view>
		</view>
		<view class="nav-rank">
			<text>排名</text>
			<text>姓名</text>
			<text>推荐录用</text>
			<text>预计积分</text>	
		</view>
		<view class="new-items" v-for="(item, index) in datalist" :key="index" :class="'myclass'+index % 2">
			<view :class="'rank'+index" class="ranknum">
				{{index+1}}
			</view>
			<view class="item-png"></view>
			<text>{{item.name}}</text>
			<text>{{item.num}}人</text>
			<text>{{item.grade}}</text>
		</view>
	</view> 
</template>

<script>
	export default{
		data(){
			return{
				datalist:[
					{name:'黄黄黄',num:'10',grade:'20000'},
					{name:'黄黄黄',num:'10',grade:'20000'},
					{name:'黄黄黄',num:'10',grade:'20000'},
					{name:'黄黄黄',num:'10',grade:'20000'},
					{name:'黄黄黄',num:'10',grade:'20000'},
					{name:'黄黄黄',num:'10',grade:'20000'},
				]
			}
		},
		methods:{
			
		}
	}
</script>

<style scoped>
	
	.rank{
		height: 600rpx;
		margin: 20rpx;
		margin-top: 60rpx;
	}
	.top-info{
		margin-right: 15rpx;
		height: 200rpx;
		display: flex;
		align-items: center;
		background-image: linear-gradient(150deg, #FFC736, #FFD24B);
	}
	.touxiang{
		margin-left: 25rpx;
		width: 150rpx;	
		height: 150rpx;
		border-radius: 50%;
		background-color: #e7d2ff;
	}
	.info1{
		margin-top: 10rpx;
		margin-left: 20rpx;
		font-size: 32rpx;
		color: #FFFFFF;
	}
	.info1 text:nth-child(2){
		margin-left: 100rpx;
	}
	.info2{
		display: flex;
		align-items: center;
		font-size: 25rpx;
		width: 500rpx;
		height: 40rpx;
		margin-left: 10rpx;
		margin-top: 20rpx;
		color: #FFC632;
		background-color: #FFFFFF;
	}
	.info2 text:nth-child(1){
		margin-left: 10rpx;
	}
	.info2 text:nth-child(2){
		margin-left: 10rpx;
	}
	.nav-rank{
		margin-right: 20rpx;
	margin-top: 30rpx;
	font-size: 25rpx;
	color: #F4661E;
	border-bottom: 5rpx solid #FFA568;
	padding-bottom: 15rpx;
	}
	.nav-rank text:nth-child(1){
	margin-left: 30rpx;
	}
	.nav-rank text:nth-child(2){
	margin-left: 100rpx;
	}
	.nav-rank text:nth-child(3){
	margin-left: 200rpx;
	}
	.nav-rank text:nth-child(4){
	margin-left: 40rpx;
	}
	.new-items{
		background-color: #FAFAFA;
		margin-right: 20rpx;
		display: flex;
		align-items: center;
		height: 150rpx;
	}
	.item-png{
		width: 120rpx;
		height: 120rpx;
		border-radius: 50%;
		background-color: #aaff7f;
		margin-left: 50rpx;
	}
	.ranknum{
		color: #999999;
		font-size: 90rpx;
		font-weight: bolder;
		margin-left: 30rpx;
	}
	.new-items text:nth-child(3){
		margin-left: 10rpx;
	}
	.new-items text:nth-child(4){
		margin-left:80rpx;
	}
	.new-items text:nth-child(5){
		margin-left: 50rpx;
	}
	.myclass1{
		background-color: #FFFFFF;
	}
	.rank0{

		color: #F86633;
	}
	.rank1{

		color: #FE8D41;
	}
	.rank2{

		color: #5385F6;
	}
</style>
