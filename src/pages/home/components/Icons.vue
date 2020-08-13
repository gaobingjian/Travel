<template>
	<div class="icons">
		<swiper :options="swiperOptions">
			<swiper-slide v-for="(page,index) of pages" :key='index'>
				<div class="icon" v-for="item of page" :key="item.id">
					<div class="icon-img">
						<img class="icon-img-content" :src=item.imgUrl>
					</div>
					<p class="icon-desc">{{ item.desc }}</p>
				</div>
			</swiper-slide>
		</swiper>
	</div>
</template>

<script type="text/javascript">
	export default {
		name : 'HomeIcons',
		props : {
			list : Array
		},
		data : function () {
			return {
				swiperOptions : {	//icon区域的图标会自动滚动，设置autoplay：false就好了
					autoplay : false
				}
			}
		},
		computed : {
			pages : function () {
				var pages = [];
				this.list.forEach(function (item, index) {
					var page = Math.floor(index / 8);
					if(!pages[page]) {
						pages[page] = [];
					}
					pages[page].push(item);
				})
				return pages;
			}
		}
	}
</script>

<style type="text/css" lang="stylus" scoped>
	@import '~styles/varibles.styl'
	@import '~styles/mixins.styl'
	.icons >>> .swiper-container
		height:0
		padding-bottom:50%
	.icons
		margin-top:.1rem
		.icon
			overflow:hidden
			height:0
			position:relative
			float:left
			width:25%
			padding-bottom:25%
			.icon-img
				position:absolute
				top:0
				left:0
				right:0
				bottom:.44rem
				border-sizing:border-box
				padding:.1rem
				.icon-img-content
					height:100%
					margin:0 auto
					display:block
			.icon-desc
				position:absolute
				left:0
				right:0
				bottom:0
				height:.44rem
				line-height:.44rem
				color:$darkTextColor
				text-align:center
				ellipsis() 
</style>





