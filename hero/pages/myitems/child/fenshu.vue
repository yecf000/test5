<template>
	<view class="all">
		<view class="touxiang">
			<image src="" mode=""></image>
			<view class="userinfo">
				<text>皇后</text>
				<text>1515161651   目前积分:100</text>
			</view>
		</view>
		<view class="cal">
			<zwyCalendar type="sign" @change="signDate" />
		</view>
	</view>
</template>

<script>
	import zwyCalendar from '@/components/zwy-calendar/zwy-calendar.vue'
	export default{
		data(){
			return{
				
			}
		},
		components:{zwyCalendar}
	}
</script>

<style scoped>
	.cal{
		margin-top: -50rpx;
	}
	.touxiang{
		background-color: #5C5CF2;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding-bottom: 50rpx;
	}
	.touxiang image{
		margin: 50rpx;
		width: 180rpx;
		height: 180rpx;
		background-color: #FFFFFF;
		border-radius: 50%;
	}
	.userinfo{
		margin-right: 60rpx;
		width: 400rpx;
		display: flex;
		flex-direction: column;
		}
	.userinfo text:nth-child(1){
		background-color: #5C5CF2;
		color: #FFFFFF;
		padding-bottom: 20rpx;
		border-bottom: #8A8FF7 1rpx solid;
	}
	.userinfo text:nth-child(2){
		background-color: #5C5CF2;
		color: #FFFFFF;
		padding-top: 20rpx;
	}
</style>
