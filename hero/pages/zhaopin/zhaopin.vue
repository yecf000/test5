<template>
	<view class="zhaopin">
		<view class="zhaopinimg">
			<image src="../../static/3.jpg" mode=""></image>
		</view>	
		<view class="zhaopinform">
				<view><text>人员姓名:</text><input type="text" value="" placeholder="请输入姓名"/></view>
				<view><text>手机号码:</text><input type="text" value="" placeholder="请输入手机号"/></view>
				<view><text>身份证号:</text><input type="text" value="" placeholder="请输入身份证号(X需要大写)"/></view>
				<view><text>面试厂区:</text><input type="text" value="" placeholder="东莞厂区"/></view>
				<view><text>面试日期:</text><input type="text" value="" placeholder="—请选择—"/></view>
				<view><text>面试职位:</text><input type="text" value="" placeholder="—不限—"/></view>
				<button type="default">提  交</button>
				<text class="b-notice">郑重承诺:音雄好汉招聘网不会直接或间接向求职者收取任何费用！</text>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				
			}
		},
		methods:{
			
		}
	}
</script>

<style scoped>
.zhaopinimg{
	margin-top: 10rpx;
}
.zhaopinimg image{
	width: 100%;
	height: 300rpx;
	
}
.zhaopinform{
	margin-top: 30rpx;
	display: flex;
	flex-direction: column;
	align-items: center;
}
.zhaopinform view{
	display: flex;
	align-items: center;
	margin: 20rpx;
}
.zhaopinform view text{
	margin-right: 30rpx;
}
.zhaopinform input{
	color: #757575;
	width: 400rpx;
	height: 60rpx;
	background-color: #E5E5E5;
	border-radius: 15rpx;
	padding: 10rpx;
}
.zhaopinform button{
	background-color: #5C5CF2;
	height: 70rpx;
	width: 550rpx;
	margin-top: 20rpx;
	color: #FFFFFF;
	display: flex;
	align-items: center;
	justify-content: center;
}
.b-notice{
	padding: 2rpx;
	margin-top: 30rpx;
	width: 600rpx;
	color: #F9BE56;
}
</style>