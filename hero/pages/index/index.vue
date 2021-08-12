<template>
	<view class="content">
	   <view class="part1">
		<view class="notice">
			<text>{{tipico}}</text>
			<text>{{phone}}</text>
		</view>
		<swiper class="swiper-box" 
			    autoplay="true" 
				interval="3000"
				duration="1000"
			    circular="true" 
			    indicatorDots="true" 
			    indicator-active-color="#8280EB" 
			>  
		<swiper-item v-for="(item, index) in Banners" :key="index" class="swiper-pic">  
		        <view>  
		            <image :src="item.PhotoPath">
					</image>
		        </view>  
		 </swiper-item>  
				</swiper-item> 
		</swiper>
		<view class="navbutton">
			<button type="default" @click="turntobaoming">直招报名</button>
			<button type="default" @click="turntobaoming">推荐入职</button>
			<button type="default" @click="turntobaoming">离职返聘</button>
		</view>
		<view class="datalist">
			<form>
				<view class="datalist-child" v-for="(item, index) in Recruitment" :key="index" @click="gotodetails(item.id)">
					<view class="datalist-1">
					<view class="datalist-1-left">
						<text>{{item.name}}</text>
						<image src="" mode=""></image>
					</view>
					<text>{{item.money}}</text>
					</view>
					<view class="datalist-2">
					<text>{{item.siteName}}</text>
					<text>{{item.workName}}</text>
					<text>{{item.workYears}}</text>
					<text>招{{item.numbers}}人</text>
					</view>
					<view class="datalist-3">
					<view>工作餐</view>
					<view>提供厂车</view>
					<view>上5休2</view>
					</view>
				</view>
			</form>
		</view>
		<button type="default" class="loadmore" @click="lodingMore">查看更多</button>
		</view>
		<view class="con-padding">
			
		</view>
		<view class="part2">
			<view class="title-button">
				<button type="default" @click="turntojtinter"></button>
				<button type="default" @click="turntokefu"></button>
			</view>
			<view class="part2-list">
				<view class="part2-list-content" v-for="(item, index) in News" :key="index" @click="gotonewsdetails(item.id)">
					<image src="" mode=""></image>
					<view class="part2-list-content-text">
						<text>{{item.title}}</text>
						<text>{{item.time}}</text>
						<text>{{item.intro}}</text>
					</view>
				</view>
			</view>
			<button type="default" class="loadmore" @click="lodingMore">查看更多</button>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				phone:'400-0891-515',
				tipico:'蒂芬妮声学唯一线上平台',
				Banners:[],
				Recruitment:[],
				News:[]
			}
		},
		onLoad() {
			this.getmydata()
			this.loding()
		},
		methods: {
			getmydata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/default/index', 
				    data: {
				    },
				    success: (res) => {
				       this.Banners=res.data.data.Banners
					   this.Recruitment=res.data.data.Recruitment
					   this.News=res.data.data.News
				    }
				});	
			},
			gotodetails(id){
				uni.navigateTo({
					url:'../zhiwei/zhiwei?id='+id
				})
			},
			gotonewsdetails(id){
				uni.navigateTo({
					url:'../news/newsdetails?id='+id
				})
			},
			turntojtinter(){
				uni.navigateTo({
					url:'../interduce/interduce'
				})
			},
			turntokefu(){
				uni.switchTab({
				         url: '../servers/servers'
				});
			},
			turntobaoming(){
				uni.navigateTo({
					url:'../zhaopin/zhaopin'
				})
			},
			lodingMore(){
				uni.showToast({
					title: '暂无更多',
					icon:'none',
					duration: 2000
				});
			},
			loding(){
				uni.showLoading({
				    title: '加载中'
				});
				
				setTimeout(function () {
				    uni.hideLoading();
				}, 500);
			}
		}
	}
</script>
<style scoped>
*{
	margin: 0;
	padding: 0;
}
.notice{
	font-size: 28rpx;
	background-color: #5C5CF2;
	display: flex;
	justify-content: space-between;
}
.notice text:nth-child(1){
	margin: 20rpx;
	color: #FFFFFF;
}

.notice text:nth-child(2){
	margin: 20rpx;
	color: #F1C445;
}

.swiper-box{
	width: 100%;
	height: 350rpx;
}
.swiper-pic image{
	width: 100%;
	height: 350rpx;
	}
.navbutton{
	margin-top: 50rpx;
	display: flex;
	justify-content: center;
	height: 150rpx;
}
.navbutton button{
	font-family: Arial, Helvetica, sans-serif;
	font-size: 35rpx;
	margin: 10rpx;
	border: none;
	color:#FFFFFF;
	width: 28%;
	height: 85rpx;
}
.navbutton button:nth-child(1){
	background-color: #2AACCE;
}
.navbutton button:nth-child(2){
	background-color: #F3BD59;
}
.navbutton button:nth-child(3){
	background-color: #F07496;
}

.datalist-child{
	border-bottom: #EEEEEE 1rpx solid;
}
.datalist-1{
	display: flex;
	justify-content: space-between;
}
.datalist-1 text{
	margin: 30rpx;
}

.datalist-1 text:nth-child(2){
	font-size: 40rpx;
	color: #FF5F3C;
	font-weight: bold;
}
.datalist-1 image{
	width: 80rpx;
	height: 30rpx;
}
.datalist-1-left{
	display: flex;
}

.datalist-2 text{
	margin-left: 25rpx;
	color:#656565
}
.datalist-3{
	display: flex;
}
.datalist-3 view{
	text-align: center;
	color: #656565;
	width: 180rpx;
	height: 50rpx;
	margin-top: 30rpx;
	margin-left: 10rpx;
	margin-bottom: 50rpx;
	border: 1rpx solid #BFBFBF;
}
.datalist-3 view:nth-child(1){
	margin-left: 30rpx;
}
.loadmore{
	font-size: 30rpx;
	margin: 0 auto;
	margin-top: 80rpx;
	margin-bottom: 80rpx;
	width: 60%;
	height: 80rpx;
	background-color: #FFFFFF;
	border-radius: 50rpx;
	border: 1rpx #D9D9D9 solid;
}
.con-padding{
	background-color: #F2F2F2;
	height: 80rpx;
	margin-top: 80rpx;
}
.part2{
	background-color: #FFFFFF;
}
.title-button{
	display: flex;
	justify-content: center;
}
.title-button button{
	width: 400rpx;
	height: 90rpx;
	background-color: #007AFF;
	margin: 30rpx;
}
.title-button button:nth-child(1){
	background: url(../../static/btn2.png);
	background-size: cover;
	
}
.title-button button:nth-child(2){
	background: url(../../static/btn1.png);
	background-size: cover;
}

.part2-list-content{
	display: flex;
	justify-content: center;
	align-items: center;
	margin-bottom: 50rpx;
}
.part2-list-content image{
	margin-left: 20rpx;
	width: 400rpx;
	height: 200rpx;
	background-color: #007AFF;
	background: url(../../static/默认封面.jpg);
	background-size: cover;
}
.part2-list-content-text{
	display: flex;
	flex-direction: column;
	margin-left:20rpx;
	padding: 10rpx;
}
.part2-list-content-text text:nth-child(2){
	color: #7D7D7D; 
	font-size: 30rpx;
}
.part2-list-content-text text:nth-child(3){
	margin-top: 8rpx;
	color: #7D7D7D; 
	font-size: 30rpx;
}
</style>
