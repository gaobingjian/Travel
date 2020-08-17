<template>
	<div>
		
		<div class="banner" @click="handleBannerClick">
		<img class="banner-img" :src="bannerImg"></img>
		<div class="banner-info">
			<div class="banner-title">{{this.sightName}}</div>
			<div class="banner-number">
				<span class="iconfont banner-icon">&#xe635;</span>
				{{this.bannerImgs.length}}
			</div>
		</div>
	</div>

	<fade-animation>
		<common-gallary
		 :imgs="bannerImgs" 
		 v-show="showGallary"
		 @close="handelGallaryClose"
		></common-gallary>
	</fade-animation>
	</div>
</template>

<script type="text/javascript">
	import CommonGallary from 'common/gallary/Gallary.vue'
	import FadeAnimation from 'common/fade/FadeAnimation.vue'
	export default {
		name : 'DetailBanner',
		props : [
			'sightName',
			'bannerImg',
			'bannerImgs' 
		],
		data () {
			return {
				showGallary : false
			}
		},
		components : {
			CommonGallary,
			FadeAnimation
		},
		methods : {
			handleBannerClick () {
				this.showGallary = true
			},
			handelGallaryClose () {
				this.showGallary = false
			}
		}
	}
</script>

<style type="text/css" lang="stylus" scoped>
	.banner
		overflow:hidden
		height:0
		padding-bottom:55%
		position:relative
		.banner-img
			width:100%
		.banner-info
			position:absolute
			left:0
			right:0
			color:#fff
			bottom:0
			display:flex
			background-image:linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
			line-height:.6rem
			.banner-title
				font-size:.32rem
				padding:0 .2rem
				flex:1
			.banner-number
				line-height:.32rem
				height:.32rem
				font-size:.24rem
				margin-top:.14rem
				padding:0 .4rem
				border-radius:.2rem
				background:rgba(0, 0, 0, 0.8)
				.banner-icon
					font-size:.24rem
</style>











