<template>
	<view class="jituanjieshao">
		<view class="jituanjieshaoimg">
			<image src="../../static/2.jpg" mode=""></image>
		</view>	
		<view class="jituancontent">
			<rich-text :nodes="detaildata.title"></rich-text>
			<rich-text :nodes="detaildata.content"></rich-text>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				detaildata:[],
			}
		},
		methods:{
			getpagedata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/default/article-detail?id=about_us', 
				    data: {
				    },
				    success: (res) => {
				       this.detaildata = res.data.data
				    }
				});	
			}
		},
		onLoad() {
			this.getpagedata()
		}
	}
</script>

<style scoped>
	.jituanjieshaoimg{
		margin-top: 10rpx;
	}
	.jituanjieshao image{
		width: 100%;
		height: 300rpx;
		
	}
	.jituancontent{
		margin-right: 30rpx;
		padding: 20rpx;
	}
</style>
