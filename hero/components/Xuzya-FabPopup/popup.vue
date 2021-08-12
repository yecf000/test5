<template>
	<view v-if="showModal">
		<view class="modal-mask" catchtouchmove="preventTouchMove"></view>
		<view class="modal-dialog" :style="{top: top +'rpx', background: background, width: width+'rpx'}"
			catchtouchmove="preventTouchMove">
			<!--顶部类型1 微信默认排版-->
			<view class='m-title-type1' :style="{color: titleColor}" v-if="topType == 1">
				{{title}}
			</view>
	
			<!--首页自定义类型2-->
			<view class='m-title-type2' :style="{color: titleColor}" v-if="topType == 2">
				{{title}}
			</view>
	
			<slot name="content"></slot>
	
			<!--底部类型1 微信默认排版 左侧取消,右侧确认-->
			<view class="modal-footer-type1" v-if="bottomType == 1">
				<view class="btn-footer-type1 btn-l-footer-type1" @tap="_onCancel">
					<text :style="{color: cancelTextColor}">{{cancelText}}</text>
				</view>
	
				<view class="btn-footer-type1" @tap="_onConfirm">
					<text :style="{color: confirmTextColor}">{{confirmText}}</text>
				</view>
			</view>
	
			<!--底部类型2 只有确认按钮-->
			<view class="modal-footer-type2" v-if="bottomType == 2" @tap="_onConfirm">
				<view class="btn-footer-type2" bindtap="_onConfirm">
					<text :style="{color: confirmTextColor}">{{confirmText}}</text>
				</view>
			</view>
	
			<!--底部类型3 自定义样式 首页-->
			<view class="modal-footer-type3" v-if="bottomType == 3" @tap="_onConfirm">
				<image src="/static/wallet.png" style="width: 351rpx;height: 79rpx;"></image>
			</view>
	
			<!--额外自定义关闭按钮-->
			<view v-if="customType == 1" style="position: absolute; bottom: -104rpx;" @tap="_onClose"
				:style="{left: width ? (width-74)/2: '288'+ 'rpx'}" >
				<image src="/static/close.png" style="width: 74rpx; height: 74rpx;"></image>
			</view>
	
			<!-- 自定义叉号关闭按钮 --> 
			<view v-if="customType == 2" style="position: absolute; top: 28rpx; right:28rpx;" @tap="_onClose">
				<image src="/static/delete.png" style="width: 32rpx; height: 32rpx;"></image>
			</view>
		</view>
	</view>
</template>

<script>
	/**
	 * Rou-popupComponents
	 * 弹窗组件
	 * 自定义弹窗内容.建议如有不满足的需求,添加组件自定义内容兼容
	 * 组件属性:
	 *      background          str(十六进制/rgb颜色)   设置弹窗背景颜色
	 *      width               number(数值,单位rpx)    弹窗宽度
	 *      title               str(标题文字)           弹窗标题
	 *      titleColor          str(十六进制/rgb颜色)   标题颜色
	 *      cancelText          str(标题文字)           取消按钮文字
	 *      cancelTextColor     str(十六进制/rgb颜色)   确定按钮文字颜色
	 *      confirmText         str(标题文字)           确定按钮文字
	 *      confirmTextColor    str(十六进制/rgb颜色)   确定按钮文字颜色
	 *      topType      str(样式类型,可在组件wxml及wxss页面自行定义,已提供几种常用模板)   顶部样式自定义类型
	 *      bottomType   str(样式类型,可在组件wxml及wxss页面自行定义,已提供几种常用模板)   底部样式自定义类型
	 *      customType   str(样式类型,可在组件wxml及wxss页面自行定义,已提供几种常用模板)   特殊(叉×关闭需求)使用
	 *
	 *      到此弹窗已经可以随心所欲的进行各种变化.是开发中按需使用属性即可.提供的属性不够? 可以参照实例.进行任意一个样式的复用重写.
	 *
	 * 组件方法:
	 *      setTopHeight()  设置组件距离顶部距离
	 *      hide()          隐藏弹窗
	 *      show()          展示弹窗
	 *      cancelEvent()   点击取消事件
	 *      confirmEvent()  点击确认事件
	 *      _onClose()      关闭按钮关闭事件
	 */
	let systemInfo = uni.getSystemInfoSync();
	export default {
		name:"popup",
		options: {
			multipleSlots: true // 在组件定义时的选项中启用多slot支持
		},
		/**
		 * 组件的属性列表
		 */
		props: {
			background: {
				type: String,
				value: '#FFFFFF',
				default: '#FFFFFF',
			},
			width:{
				type: Number,
				value: 0,
			},
			title: {
				type: String,
				value: '标题',
				default: '标题',
			},
			titleColor: {
				type: String,
				value: '#000000',
				default: '#000000',
			},
			cancelText: {
				type: String,
				value: '取消',
				default: '取消',
			},
			cancelTextColor: {
				type: String,
				default: '#ff0000'
			},
			confirmText: {
				type: String,
				default: '确认'
			},
			confirmTextColor: {
				type: String,
				default: '#00aaff'
			},
			topType: {
				type: String,
				value: '1'
			},
			bottomType: {
				type: String,
				value: '1'
			},
			customType: {
				type: String,
				value: '0'
			},
		},

		/**
		 * 组件的初始数据
		 */
		data(){
			return {
				showModal: false,
				top: 0,                 //设置弹窗与顶部的距离
			}
		},

		/**
		 * 组件的方法列表
		 */
		methods: {
			//return触摸事件
			preventTouchMove: function () {
				console.log('stop user scroll it!');
				return
			},
			//设置弹窗高度
			setTopHeight(num) {
				this.top = num
			},
			//自定义的关闭按钮
			setCustomType(type) {
				this.customType = type
			},
			//隐藏弹窗
			hide() {
				this.showModal = false
			},
			//显示弹窗
			show() {
				this.showModal = true
			},
			//取消事件
			_onCancel() {
				this.$emit("cancelEvent")
			},
			// 确认事件
			_onConfirm() {
				this.$emit("confirmEvent")
			},
			//自定义关闭
			_onClose() {
				this.$emit("onClose")
			}
		}
	}
</script>

<style>
/* 蒙层 */
.modal-mask {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    background: #000;
    opacity: 0.5;
    overflow: hidden;
    z-index: 1000;
    color: #fff;
}
/* 弹框 */
.modal-dialog{
    font-size: 30rpx;
    width:646rpx;
    position: fixed;
    top: 5%;
    left:0;
    right: 0;
    margin:auto;
    z-index: 1500;
    background: #ffffff;
    border-radius: 16rpx;
    display: flex;
    flex-direction: column;
}


/*头部类型1样式*/
.m-title-type1 {
    height: 88rpx;
    line-height: 88rpx;
    text-align: center;
    align-self: stretch;
    font-size: 36rpx;
    margin-top: 28rpx;
}
/*头部类型1样式结束*/


/*头部类型2样式**/
.m-title-type2 {
    height: 88rpx;
    line-height: 88rpx;
    text-align: center;
    align-self: stretch;
    font-size: 36rpx;
}
/**头部类型2样式结束*/



/*底部类型1样式*/
.modal-footer-type1{
    display: flex;
    height: 100rpx;
    border-top: 1rpx solid #E5E5E5;
    align-items: center;
    justify-content: center;
}
.btn-footer-type1{
    height: 100rpx;
    width: 280rpx;
    font-size: 36rpx;
    display: flex;
    align-items: center;
    justify-content: center;
}
.btn-l-footer-type1{
    border-right: 1rpx solid #E5E5E5;
    color: #333;
}
/*底部类型1样式结束*/


/*底部类型2样式*/
.modal-footer-type2{
    display: flex;
    height: 100rpx;
    border-top: 1rpx solid #E5E5E5;
    align-items: center;
    justify-content: center;
}
.btn-footer-type2{
    height: 100rpx;
    width: 280rpx;
    font-size: 36rpx;
    display: flex;
    align-items: center;
    justify-content: center;
}
/*底部类型2样式结束*/

/*底部类型3样式*/
.modal-footer-type3{
    display: flex;
    height: 138rpx;
    align-items: center;
    justify-content: center;
}
/*底部类型3样式结束*/
</style>
