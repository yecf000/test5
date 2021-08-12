<template>
	<view class="myitems">
		<view class="touxiang">
			<image src="" mode=""></image>
			<view class="userinfo">
				<text>皇后</text>
				<text>1515161651</text>
			</view>
		</view>
		<view class="sec-items">
			<view class="sec-item-child">
				<image src="" mode="" class="img1"></image>
				<view class="content">
					<text>1000</text>
					<view>目前积分</view>
				<button type="default" @click="turntopagecal"><text>查看详情</text></button>
				</view>
			</view>
			<view class="sec-item-child">
				<image src="" mode="" class="img2"></image>
				<view class="content">
					<text>10/8</text>
					<view>推荐/录用</view>
				<button type="default" @click="turntopage3"><text>查看详情</text></button>
				</view>
			</view>
		</view>
		<view class="jianxi">
		</view>
		<view class="connect-items">
			<view @click="turntopage1">
				<image src="" mode="" class="con-icon icon-1"></image>
				<text>我的资料</text>
				<text>〉</text>
			</view>
			<view @click="turntopage2">
				<image src="" mode="" class="con-icon icon-2"></image>
				<text>报名记录</text>
				<text>〉</text>
			</view>			
			<view @click="turntopage3">
				<image src="" mode="" class="con-icon icon-3"></image>
				<text>推荐记录</text>
				<text>〉</text>
			</view>			
			<view @click="turntopage4">
				<image src="" mode="" class="con-icon icon-4"></image>
				<text>猎人排名</text>
				<text>〉</text>
			</view>			
			<view @click="turntopage5">
				<image src="" mode="" class="con-icon icon-5"></image>
				<text>幸运转盘</text>
				<text>〉</text>
			</view>			
			<view @click="turntopage6">
				<image src="" mode="" class="con-icon icon-6"></image>
				<text>积分兑换</text>
				<text>〉</text>
			</view>			
			<view @click="open">
				<image src="" mode="" class="con-icon icon-7"></image>
				<text>我的海报</text>
				<text>〉</text>
			</view>			
			<view @click="turntopage8">
				<image src="" mode="" class="con-icon icon-8"></image>
				<text>联系客服</text>
				<text>〉</text>
			</view>
			
			<view class="tanchuceng">
			<uni-popup ref="popup" type="bottom" class="">
			<view class="haibao">
				<image src="" mode=""></image>
				<button type="default"><text>保存图片</text></button>
				<view>
					保存至相册可以分享到朋友圈
				</view>
			</view>
			</uni-popup>
			
			</view>
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
			turntopage1(){
				uni.navigateTo({
					url:'./mydetails'
				})
			},
			turntopage2(){
				uni.navigateTo({
					url:'./tuijian'
				})
			},
			turntopage3(){
				uni.navigateTo({
					url:'./tuijian'
				})
			},
			turntopage4(){
				uni.navigateTo({
					url:'./rank'
				})
			},
			turntopage5(){
				uni.navigateTo({
					url:'./choujiang'
				})
			},
			turntopage6(){
				uni.navigateTo({
					url:'./jifenduihuan'
				})
			},
			turntopage7(){
				uni.navigateTo({
					url:'./newspaper'
				})
			},
			turntopage8(){
				uni.switchTab({
					url:'../servers/servers'
				})
			},
			turntopagecal(){
				uni.navigateTo({
					url:'./child/fenshu'
				})
			},
			open(){
			  this.$refs.popup.open('center')
			}
		},
		onLoad() {
			
		}
	}
</script>

<style>
	.touxiang{
		background-color: #5C5CF2;
		display: flex;
		justify-content: space-between;
		align-items: center;
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
		color: #FFFFFF;
		padding-bottom: 20rpx;
		border-bottom: #8A8FF7 1rpx solid;
	}
	.userinfo text:nth-child(2){
		color: #FFFFFF;
		padding-top: 20rpx;
	}
	.sec-items{
		display: flex;
	}
	.sec-item-child{
		margin: 20rpx;
		display: flex;
	}
	.sec-item-child image{
		margin-top: 30rpx;
		width: 100rpx;
		height: 100rpx;

	}
	.sec-item-child:nth-child(2){
		margin-left: 50rpx;
	}
	.content{
		margin-left: 20rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.content button{
		display: flex;
		align-items: center;
		justify-content: center;
		padding-top: -5px;
		border-radius: 23rpx;
		margin-top: 10rpx;
		height: 50rpx;
		width: 180rpx;
		background-color: #238FD8;
	}
	.content button text{
		font-size: 22upx;
		color: #FFFFFF;
	}
	
	.content text{
		font-size: 55rpx;
	}
	
	.content view{
		font-size: 25rpx;
	}
	.img1{
		background: url(../../static/user_1.png);
		background-size: cover;
	}
	.img2{
		background: url(../../static/user_2.png);
		background-size: cover;
	}
	.jianxi{
		height: 30rpx;
		background-color: #F7F7F7;
	}
	.connect-items view{
		margin-left: 20rpx;
		margin-right: 50rpx;
			padding: 20rpx;
			display: flex;
			align-items: ;
			border-bottom: #D1D1D1 1rpx solid;
	}
	.connect-items view:nth-child(9){
		border: none;
	}
	
		.connect-items view text{
			color: #656565;
			margin-top: 5rpx;
			width: 100%;
		}
		
	.connect-items view text:nth-child(3){
		text-align: end;
	}
	.connect-items view text:nth-child(2){
		margin-left: 10rpx;
	}
	.con-icon{
		width: 150rpx;
		height: 60rpx;
	}
	.icon-1{
		background: url(../../static/user_m1.png);
		background-size: cover;
	}
	.icon-2{
		background: url(../../static/user_m2.png);
		background-size: cover;
	}
	.icon-3{
		background: url(../../static/user_m3.png);
		background-size: cover;
	}
	.icon-4{
		background: url(../../static/user_m4.png);
		background-size: cover;
	}
	.icon-5{
		background: url(../../static/user_m5.png);
		background-size: cover;
	}
	.icon-6{
		background: url(../../static/user_m6.png);
		background-size: cover;
	}
	.icon-7{
		background: url(../../static/user_m7.png);
		background-size: cover;
	}
	.icon-8{
		background: url(../../static/user_m8.png);
		background-size: cover;
	}
	.tanchuceng{
		margin-left: 50rpx;
	}
	.haibao{
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 650rpx;
		height: 600rpx;
		background-color: #FFFFFF;
		text-align: center;
		border-radius: 15rpx;
	}
	.haibao image{
		height: 480rpx;
		width: 650rpx;
		background: url(../../static/haibao.png);
		background-size: cover;
		margin-bottom: 30rpx;
	}

	.haibao button{
		display: flex;
		align-items: center;
		background-color:#5B5CF2 ;
		height: 70rpx;
		width: 450rpx;
	}
	.haibao button text{
		margin-top: -2rpx;
		padding: 5rpx;
		color: #FFFFFF;
		font-size: 33rpx;
	}
	.haibao view{
		margin-left: 50rpx;
		font-size: 28rpx;
		color: #555555;
		border-bottom: none;
	}
	.tanchuceng view{
		margin-left: 30rpx;
	}
</style>
