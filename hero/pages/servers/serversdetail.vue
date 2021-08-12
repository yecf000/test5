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
		<view class="nav_items">
			<view class="nav_item" v-if="isActive==1">
			AAA
			</view>
			<view class="nav_item" v-if="isActive==2">
			BBB
			</view>
			<view class="nav_item" v-if="isActive==3">
			CCC
			</view>
			<view class="nav_item" v-if="isActive==4">
			DDD
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				isActive: 1,
			}
		},
		methods:{
			chenked(type) {
				this.isActive = type
			},
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
		margin-top: 30rpx;
		display: flex;
		justify-content: space-around;
		color: #676767;
		border-bottom: #E8E8E8 1rpx solid;
	}
</style>
