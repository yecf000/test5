<template>
	<view class="jilu">
		<view class="title-png">
			<image src="../../static/4.jpg" mode=""></image>		
		</view>
		<view class="nav">
			<text :class="t1select" @click="changecon1" class="childitems">报名记录</text>
			<text :class="t2select" @click="changecon2" class="childitems">推荐记录</text>
		</view>
		<view class="con1" v-if="show">
			<view class="form">
				<view class="form-nav">
					<text>时间</text>
					<text>姓名</text>
					<text>状态</text>
				</view>
				<view class="data">
					<text>2020-03-12</text>
					<text>一枪</text>
					<text>成功录取</text>
				</view>
				<view class="shijianzhou">
					<uni-steps class="unisteps" activeColor="#F27698" :options="shijianxian" :active="3"></uni-steps>
				</view>
				<view class="jiangli">
					<view>
						<text>成功录取</text>
						<text>奖励100积分</text>
						<button type="default" :class="bt" class="butcolor1">提取奖励</button>
					</view>
					<view>
						<text>入职满1个月</text>
						<text>奖励100积分</text>
						<button type="default" :class="bt">提取奖励</button>
					</view>
					<view>
						<text>入职满2个月</text>
						<text>奖励100积分</text>
						<button type="default" :class="bt">提取奖励</button>
					</view>
					<view>
						<text>入职满3个月</text>
						<text>奖励100积分</text>
						<button type="default" :class="bt">提取奖励</button>
					</view>
					<view>
						<text>入职满6个月</text>
						<text>奖励100积分</text>
						<button type="default" :class="bt">提取奖励</button>
					</view>
					<view>
						<text>流程结束</text>		
					</view>
				</view>
			</view>
			<view class="form form2">
					<view class="form-nav">
						<text>时间</text>
						<text>姓名</text>
						<text>状态</text>
					</view>
					<view class="data">
						<text>2020-03-12</text>
						<text>一枪</text>
						<text>成功录取</text>
					</view>
				</view>
		</view>
		<view class="con2" v-if="!show">
			222
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				t1select:'selected',
				t2select:'unselected',
				show:true,
				shijianxian:[
					{title: '提交材料'}, 
					{title: '等待审核'}, 
					{title: '等待面试'}, 
					{title: '到场面试'},
					{title: ''},
					{title: ''},
				],
				bt:'butcolor'
			}
		},
		methods:{
			changecon1(){
				this.show = true
				this.t1select ="selected"
				this.t2select='unselected'
			},
			changecon2(){
				this.show = false
				this.t1select ="unselected"
				this.t2select='selected'
			}
		},
		onLoad() {
			
		}
	}
	
</script>

<style scoped>
	.title-png{
		margin-top: 10rpx;
		height: 300rpx;
	}
	.title-png image{
		width: 101%;
		height: 300rpx;
	}
	.nav{
		width: 92%;
		margin: 30rpx;
		margin-top: 50rpx;
		padding-bottom: 15rpx;
		border-bottom: 1px #D1D1D1 solid;
	}
	.nav text{
		padding: 10rpx;
	}
	.unselected{
		background-color: #F2F2F2;
		color: #636363;

	}
	.selected{
		background-color: #5C5CF2;
		color: #FFFFFF;	

	}
	
	.nav text:nth-child(2){
		margin-left: 5rpx;
	}
	.form{
		font-size: 35rpx;
		width: 92%;
		height: 800rpx;
		margin: 0 auto;
	}
	.form-nav{
		font-size: 30rpx;
		display: flex;
		align-items: center;
		height: 60rpx;
		background-color: #5C5CF2;
		color: #FFFFFF;
	}
	.form-nav text:nth-child(1){
		width: 200rpx;
		margin: 0 auto;
	}
	.form-nav text:nth-child(2){
		width: 80rpx;
		margin: 0 auto;
	}
	.form-nav text:nth-child(3){
		width: 80rpx;
		margin: 0 auto;
		
	}
	.data{
		font-size: 27rpx;
		display: flex;
		align-items: center;
		height: 60rpx;
		background-color: #F2F2F2;
	}
	.data text:nth-child(1){
		margin-left: -50rpx;
		width: 320rpx;
		text-align: center;
	}
	.data text:nth-child(2){
		margin-left: 80rpx;
		width: 200rpx;
		text-align: center;
	}
	.data text:nth-child(3){
		width: 250rpx;
		text-align: center;
		color: #F07496;
	}
	.data text{
		color: #888888;
	}
	.shijianzhou{
		height: 100px;
		background-color: #FFFFFF;
	}
	.jiangli view{
		display: flex;
		align-items: center;
		margin-top: 5rpx;
		height: 100rpx;
		background-color: #F7F7F7;
	}
	.jiangli view text:nth-child(1){
		width: 200rpx;
		margin-left: 20rpx;
		color: #888888;
		font-size: 30rpx;
	}
	.jiangli view text:nth-child(2){
		width: 200rpx;
		margin-left: 20rpx;
		color: #F07496;
		font-size: 25rpx;
	}
	.butcolor{
			color: #FFFFFF;
			background-color:#CCCCCC ;
			border-radius: 0;
			font-size: 25rpx;
			width: 160rpx;
			margin-left: 60rpx;
	}
	.butcolor1{
		background-color: #F07496;
	}
		
	.form2{
		margin-top: 200rpx;
		height: 200rpx;
	}
</style>
