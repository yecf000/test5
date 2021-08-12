<template>
	<view class="news">
		<view class="newsimg">
			<image src="../../static/5.jpg" mode=""></image>
		</view>
		<view class="dayi-nav">
			<text :class="{'active':isActive==1}" @click="chenked(1)">集团</text>
			<text :class="{'active':isActive==2}" @click="chenked(2)">东莞</text>
			<text :class="{'active':isActive==3}" @click="chenked(3)">惠州</text>
			<text :class="{'active':isActive==4}" @click="chenked(4)">东城</text>
			<text :class="{'active':isActive==5}" @click="chenked(5)">行业资讯</text>
		</view>
		<view class="nav_items" >
			<view class="nav_item" v-if="isActive==1">
				<view class="part2-list-content" v-for="(item, index) in list" :key="index" @click="gotonewsdetails(item.id)">
					<view class="new-left">
						<view class="news-png">
						</view>
					</view>
					<view class="part2-list-content-text">
						<text>{{item.title}}</text>
						<text>{{item.addtime}}</text>
						<text>{{item.intro}}</text>
					</view>
				</view>
				<u-loadmore :status="status" :load-text="loadText" @loadmore="getmoreList()"/>
			</view>
			<view class="nav_item" v-if="isActive==2">
				<view class="part2-list-content" v-for="(item, index) in list" :key="index" @click="gotonewsdetails(item.id)">
				<view class="new-left">
					<view class="news-png">
					</view>
				</view>
				<view class="part2-list-content-text">
					<text>{{item.title}}</text>
					<text>{{item.addtime}}</text>
					<text>{{item.intro}}</text>
				</view>
				</view>
				<u-loadmore :status="status" :load-text="loadText" @loadmore="getmoreList()"/>
			</view>
			<view class="nav_item" v-if="isActive==3">
				<view class="part2-list-content" v-for="(item, index) in list" :key="index" @click="gotonewsdetails(item.id)">
				<view class="new-left">
					<view class="news-png">
					</view>
				</view>
				<view class="part2-list-content-text">
					<text>{{item.title}}</text>
					<text>{{item.addtime}}</text>
					<text>{{item.intro}}</text>
				</view>
				</view>
				<u-loadmore :status="status" :load-text="loadText" @loadmore="getmoreList()"/>
			</view>
			<view class="nav_item" v-if="isActive==4">
				<view class="part2-list-content" v-for="(item, index) in list" :key="index" @click="gotonewsdetails(item.id)">
				<view class="new-left">
					<view class="news-png">
					</view>
				</view>
				<view class="part2-list-content-text">
					<text>{{item.title}}</text>
					<text>{{item.addtime}}</text>
					<text>{{item.intro}}</text>
				</view>
				</view>
				<u-loadmore :status="status" :load-text="loadText" @loadmore="getmoreList()"/>
			</view>
			<view class="nav_item" v-if="isActive==5">
				<view class="part2-list-content" v-for="(item, index) in list" :key="index" @click="gotonewsdetails(item.id)">
				<view class="new-left">
					<view class="news-png">
					</view>
				</view>
				<view class="part2-list-content-text">
					<text>{{item.title}}</text>
					<text>{{item.addtime}}</text>
					<text>{{item.intro}}</text>
				</view>
				</view>
				<u-loadmore :status="status" :load-text="loadText" @loadmore="getmoreList()"/>
			</view>
		</view>
	</view>
</template>

<script>
	import wsLoadMore from '../../components/wsure-load-more/load-more.vue'
	export default{
		components:{
			wsLoadMore
		},
		data(){
			return{
				isActive: 1,
				listItem:'cat_id=1',
				status: 'loadmore',
				list: 0,
				pageNum: 1,
				pageSize:5,
				loadText: {
				loadmore: '点击加载更多...',
				loading: '努力加载中...',
				nomore: '没有更多了'
				},
			}
		},
		methods:{
			chenked(type) {
				this.isActive = type
				this.listItem = 'cat_id='+type
				this.getmydata()
			},	    
			onLoad() {
				this.getmydata()
				this.loding()
			},
			getmoreList() {
                this.status = 'loading';
                setTimeout(() => {
                    this.pageSize += this.pageSize;
                    this.getmydata();
                }, 1000)
				
            },
			
			getmydata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/default/topic-list?'+this.listItem,
				    data: {
						page:this.pageNum,
						row:this.pageSize,
				    },
					success: (res) => {
					this.list=res.data.data.list
					this.total=res.data.data.list.length
					if(this.pageSize >= this.total)
					{
					this.status = 'nomore';                       
					}
					else{
					this.status = 'loadmore';
					}
					},
					 fail: (resq) => {
					console.log(resq)
					uni.showToast({
					title: "请求超时！",
					icon: 'none',
					duration: 2000
					});
					},
					
				});	
			},
			gotonewsdetails(id){
				uni.navigateTo({
					url:'../news/newsdetails?id='+id
				})
			},
			loding(){
				uni.showLoading({
				    title: '加载中'
				});
				
				setTimeout(function () {
				    uni.hideLoading();
				}, 1000);
			},
		},
		onReady() {

		}
	}
</script>

<style scoped>
	.active{
		margin-bottom: -6rpx;
		color: #5C5CF2;
		border-bottom: 10rpx #5C5CF2 solid;
	}
	.nav_item{
		margin: 20rpx;
	}
	.newsimg{
		margin-top: 10rpx;
	}
	
	.newsimg image{
		width: 100%;
		height: 300rpx;
	}
	.dayi-nav{
		margin: 0 auto;
		width: 95%;
		margin-top: 30rpx;
		display: flex;
		justify-content: space-around;
		color: #676767;
		border-bottom: #E8E8E8 1rpx solid;
	}
	.dayi-nav text{
		padding-bottom: 10rpx;
		width: 80rpx;
		text-align: center;
	}
	.dayi-nav text:nth-child(5){
		text-align: center;
		width: 150rpx;
	}

	.part2-list-content{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.part2-list-content image{
		width: 400rpx;
		height: 200rpx;
		background: url(../../static/ttt.jpg);
		background-size: cover;
	}
	.news-png{
		width: 200rpx;
		height: 200rpx;
		background: url(../../static/ttt.jpg);
		background-size: cover;
	}
	.part2-list-content-text{
		display: flex;
		flex-direction: column;
		margin: 30rpx;
	}
	.part2-list-content-text text:nth-child(1){
	}
	.part2-list-content-text text:nth-child(2){
		color: #777777;
		font-size: 30rpx;
	}
	.part2-list-content-text text:nth-child(3){
		margin-top: 5rpx;
		color: #777777;
	}
</style>
