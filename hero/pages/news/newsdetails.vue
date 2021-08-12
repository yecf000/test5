<template>
	<view class="news">
		<view class="newsimg">
			<image src="../../static/5.jpg" mode=""></image>
		</view>
		<view class="newscontent">
			<view class="newstitle">
				<text>{{this.detaildata.title}}</text>
				<text>{{this.detaildata.addtime}}</text>
			</view>
			<view>
				<image src="" mode="" class="backimg"></image>
			</view>
			<view class="article">
				<rich-text :nodes="this.detaildata.content"></rich-text>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				pageid:'',
				detaildata:[]
			}
		},
		methods:{
			getpagedata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/default/topic-details?id='+this.pageid, 
				    data: {
				    },
				    success: (res) => {
				       this.detaildata=res.data.data
				    }
				});	
			}
		},
		onLoad(option) {
			this.pageid=option.id;
			this.getpagedata()
		}
	}
</script>

<style scoped>

	.newsimg{
		margin-top: 10rpx;
	}
	.newsimg image{
		width: 100%;
		height: 300rpx;
	}
	.newscontent{
		margin: 30rpx;
	}
	.newstitle{
		display: flex;
		flex-direction: column;
		border-bottom: #DCDCDC 1rpx solid;
	}
	.newstitle text:nth-child(1){
		font-size: 35rpx;
	}
	.newstitle text:nth-child(2){
		margin-top: 10rpx;
		margin-bottom: 25rpx;
		color: #676767;
		font-size: 30rpx;
	}
	.backimg{
		margin-top: 30rpx;
		width: 100%;
		background: url(../../static/ttt.jpg);
		background-size: cover;
	}
	.article{
		font-size: 35rpx;
		color: #676767;
		margin-top: 20rpx;
	}
</style>
