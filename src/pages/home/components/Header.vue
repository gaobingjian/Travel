<template>
	<div class="header">
		<div class="header-left">
			<div class="iconfont back-icon">&#xe624;</div>
		</div>
		<div class="header-input">
			<span class="iconfont">&#xe632;</span>
			输入城市/景点/游玩主题
		</div>
		<router-link to="/city">
			<div class="header-right">
				{{ this.city }}
				<span class="iconfont arrow-icon">&#xe64a;</span>
			</div>
		</router-link>
	</div>
</template>

<script type="text/javascript">
  import {mapState} from 'vuex'
export default {
  name: 'HomeHeader',
  computed : {
    ...mapState(['city'])
  }
}
</script>
<!-- ~@相当于src目录 -->
<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	@import '~styles/mixins.styl'
	.header
		display:flex
		line-height:$headerHeight
		background-color:$bgColor
		color:#fff
		.header-left
			float:left
			width:.64rem
			.back-icon
				text-align:center
				font-size:.4rem
		.header-input
			color:#ccc
			margin-top:.12rem
			height:.64rem
			line-height:.64rem
			margin-left:.2rem
			padding-left:.2rem
			background-color:#fff
			border-radius:0.1rem
			flex:1
		.header-right
			float:right
			min-width:1.04rem
			padding: .1rem
			text-align:center
			color:#fff
			.arrow-icon
				font-size:.24rem
</style>
