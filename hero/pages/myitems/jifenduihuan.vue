<template>
	<view class="duihuan">
		<view class="duihuanlist" v-for="(item, index) in datalist" :key="index" :class="'myclass'+index % 2">
			<view class="child-items">
				<view class="tou-icon">
				
				</view>
			<view class="neirong">
				<view class="content-1">
					<text>{{item.title}}</text>
					<text>{{item.limit}}</text>
				</view>
				<view class="content-2">
					<text>￥{{item.price}}积分</text>
					<button type="default"><text>立即兑换</text></button>
				</view>
			</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				datalist:[
					{title:'人马大饭堂20圆优惠券',limit:'满100圆使用',price:'200'},
					{title:'人马大饭堂20圆优惠券',limit:'满100圆使用',price:'200'},
					{title:'人马大饭堂20圆优惠券',limit:'满100圆使用',price:'200'},
					{title:'人马大饭堂20圆优惠券',limit:'满100圆使用',price:'200'},
				],
			}
		}
	}
	
</script>

<style scoped>
	.child-items{
		display: flex;
		align-items: center;
		padding: 20rpx;
		height: 200rpx;
	}
	.tou-icon{
		margin-left: 20rpx;
	width: 180rpx;
	height: 180rpx;
	border-radius: 50%;
	background-color: #BFBFBF;
	}
	.content-1{
		font-size: 30rpx;
		margin-left: 30rpx;
		width: 450rpx;
		display: flex;
		flex-direction: column;
		border-bottom: 1px #D1D1D1 solid;
		padding-bottom: 20rpx;
	}
	.content-2{
		display: flex;
		justify-content: space-between;
		padding-top: 20rpx;
		margin-left: 30rpx;
	}
	.content-2 button{
		margin-left: 60px;
		height: 55rpx;
		background-color: #FE8D41;
		display: flex;
		align-items: center;
	}
	.content-2 button text{
		font-size: 25rpx;
		color: #FFFFFF;
	}
	.content-2 text{
		font-size: 38rpx;
		color: #4F82F7;
	}
	.content-1 text:nth-child(2){
		margin-top: 5rpx;
		color: #666666;
		font-size: 28rpx;
	}
	.duihuanlist{

	}
	.myclass1{
		background-color: #F6F6F6;
	}
</style>
