
<template>
	<div>
		<transition>
			<slot></slot>	
		</transition>
	</div>
</template>

<script type="text/javascript">
	export default {
		name : 'FadeAnimation'
	}
</script>

<style type="text/css" lang="stylus" scoped>
	.v-enter .v-leave-to
		opacity : 0
	.v-enter-active .v-leave-active
		transition : opacity .5s
</style>











