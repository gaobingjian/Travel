<template>
	<div class="wrapper">
		<swiper :options="swiperOptions" v-if="showSwiper">
			<!-- 一开始list是空数组，导致数据请求之后，list有数据后，轮播图从第四张开始，用v-if可以解决 -->
		   	<swiper-slide v-for="item of list" :key="item.id">
		   		<img class="swiper-img" :src=item.imgUrl>
		   	</swiper-slide>
		    <div class="swiper-pagination" slot="pagination"></div>
		 </swiper>
	</div>
</template>

<script>
	export default {
		name : 'HomeSwiper',
		props : {
			list : Array
		},
		data : function () {
			return {
				swiperOptions : {
					pagination : '.swiper-pagination',  //轮播图的小圆点
					loop : true
				}
			}
		},
		computed : {
			showSwiper : function () {
				return this.list.length
			}
		}
	}
</script>

<style lang="stylus" scoped>
	.wrapper >>> .swiper-pagination-bullet-active 
		background:#fff 
	.wrapper
		width:100%
		height:0
		overflow:hidden
		padding-bottom:26.66%
		background:#ccc
		.swiper-img
			height:2rem
			width:100%
</style>
