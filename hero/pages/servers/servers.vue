<template>
	<view class="dayijiehuo">
		<view class="dayijiehuoimg">
			<image src="../../static/6.jpg" mode=""></image>
		</view>	 
		<view class="dayi-nav">
			<text :class="{'active':isActive==1}" @click="chenked(1)">集团</text>
			<text :class="{'active':isActive==2}" @click="chenked(2)">东莞</text>
			<text :class="{'active':isActive==3}" @click="chenked(3)">惠州</text>
			<text :class="{'active':isActive==4}" @click="chenked(4)">东城</text>
		</view>
		<view  class="nav_items" v-for="(item, index) in detaildata" :key="index" :class="'myclass'+item.id % 2">
			<view class="nav_item" v-if="isActive==1">
			<text class="question"><text>Q</text>:  {{item.problem}}</text>
			<view class="hengxian"></view>
			<text class="anwser">{{item.answer}}</text>
			</view>
			<view class="nav_item" v-if="isActive==2">
			<text class="question"><text>Q</text>:  {{item.problem}}</text>
			<view class="hengxian"></view>
			<text class="anwser">{{item.answer}}</text>
			</view>
			<view class="nav_item" v-if="isActive==3">
			<text class="question"><text>Q</text>:  {{item.problem}}</text>
			<view class="hengxian"></view>
			<text class="anwser">{{item.answer}}</text>
			</view>
			<view class="nav_item" v-if="isActive==4">
			<text class="question"><text>Q</text>:  {{item.problem}}</text>
			<view class="hengxian"></view>
			<text class="anwser">{{item.answer}}</text>
			</view>
		</view>
		<view class="bot-png">
			<image src="../../static/kf.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				myclass:'myclass1',
				isActive: 1,
				detaildata:[],
				listItem :'cat_id=1'
			}
		},
		methods:{
			chenked(type) {
				this.listItem ='cat_id='+type
				this.isActive = type
				this.getpagedata()
				uni.showLoading({
				    title: '加载中'
				});
				
				setTimeout(function () {
				    uni.hideLoading();
				}, 500);
			},
			getpagedata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/default/qa?'+this.listItem, 
				    data: {
				    },
				    success: (res) => {
				       this.detaildata=res.data.data.qa_list
				    }
				});	
			},
			loding(){
				uni.showLoading({
				    title: '加载中'
				});
				
				setTimeout(function () {
				    uni.hideLoading();
				}, 1000);
			}
		},
		onLoad() {
			this.getpagedata()
			this.loding()
		}
	}
</script>

<style scoped>
	.active{
		color: #5C5CF2;
		border-bottom: 10rpx #5C5CF2 solid;
	}
	.dayijiehuoimg{
		margin-top: 10rpx;
	}
	.dayijiehuo image{
		width: 100%;
		height: 300rpx;
	}
	.dayi-nav{
		width: 700rpx;
		margin-left: 20rpx;
		margin-top: 30rpx;
		display: flex;
		justify-content: center;
		color: #676767;
		border-bottom: #E8E8E8 1rpx solid;
	}
	.dayi-nav text:nth-child(1){
		margin-left: -0rpx;
	}
	.dayi-nav text{
		margin-left: 80rpx;
		text-align: center;
		width: 80rpx;
	}
	.nav_items{
		padding: 20rpx;
		margin: 30rpx;
	}
	.hengxian{
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		border-bottom: 2rpx #DCDCDC solid;
	}
	.nav_item{
		margin-bottom: 15rpx;	
		}
	.question{

	}
	.question text{
		
		color: #FFAF71;
	}
	.anwser{
		color: #626262;
	}

	.myclass1{
		background-color: #F1F1F1;
	}
	.bot-png{
		display: flex;
		justify-content: center;
	}
	.bot-png image{
		padding-top: 20rpx;
		margin: 0 auto;
		width: 75%;
		height: 80rpx;
		margin-bottom: 30rpx;
	}
</style>
