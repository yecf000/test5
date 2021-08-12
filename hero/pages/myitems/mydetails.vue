<template>
	<view class="mydetails">
		<view>
			<text>我的头像</text>
			<view class="getnowtouxiang">
				<view class="tou-icon">
					
				</view>
				<text>〉</text>
			</view>
		</view>
		<view>
			<text>我的昵称</text>
			<text></text>
		</view>
		<view>
			<text>性别</text>
			<text>男 〉</text>
		</view>
		<view>
			<text>邮箱</text>
			<text></text>
		</view>
		<view>
			<text>电话</text>
			<text></text>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
			
			}	
		}
	}
</script>

<style scoped>
	.mydetails view{
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 100rpx;
		border-bottom: 1px solid #D1D1D1;
	}
	.mydetails view text{
		margin-left: 50rpx;
	}
	.mydetails view text:nth-child(2){
		margin-right: 50rpx;
	}
	.getnowtouxiang{
		background: url();
	}
	.getnowtouxiang view{
		margin-right: -30rpx;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		background-color: #777777;
		width: 90rpx;
		height: 90rpx;
		border-radius: 50%;
	}
	.getnowtouxiang text{
		margin-right: 50rpx;
	}

</style>
