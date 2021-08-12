<template>
	<view class="">
		<rich-text :nodes="this.data"></rich-text>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				data:''
			}
		},
		onLoad() {
			this.getmydata()
		},
		methods:{
			getmydata(){
				uni.request({
				    url: 'https://test.chudaikeji.com/proj-wxs-yxhh-zp/web/index.php/api/user/index', 
				    data: {
				    },
				    success: (res) => {
				       this.data=res.data
				    }
				});	
			},
		}
	}
</script>

<style>
</style>
